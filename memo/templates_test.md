# 変数
## GUID
export GUID=4b1a
## CONSOLE_URL
export CONSOLE_URL=https://console-openshift-console.apps.cluster-${GUID}.${GUID}.example.opentlc.com
## MASTER_URL
export MASTER_URL=https://api.cluster-${GUID}.${GUID}.example.opentlc.com:6443
## PAMをインストールするProject名
export OCP_PROJECT=rhpam-test
## USER
export USER=user1
## PAM_SECRETS_TEMPLATE_YML
export PAM_SECRETS_TEMPLATE_YML=https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml
## PAMのアプリケーション名
export APP_NAME=rhpam7

# OPENSHIFT へのログイン
oc login ${MASTER_URL} -u opentlc-mgr -p r3dh4t1! --insecure-skip-tls-verify=true

# Install Java
## get openjdk image stream
oc get is java -n openshift
## install java image stream
oc apply -n openshift -f https://raw.githubusercontent.com/jboss-openshift/application-templates/master/openjdk/openjdk18-image-stream.json

# Install PAM templates
## Check if PAM ImageStreams exists
oc get is/rhpam-businesscentral-rhel8 -n openshift
## Import the RHPAM ImageStreams into the cluster
oc create -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.0.GA/rhpam79-image-streams.yaml  -n openshift
## Check if RHPAM Authoring Template exists
oc get template/rhpam79-authoring -n openshift
## Import the RHPAM Authoring Template into the cluster.
oc create -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.0.GA/templates/rhpam79-authoring.yaml -n openshift
## Check if RHPAM Trial Template exists
oc get template/rhpam79-trial-ephemeral -n openshift
## Import the RHPAM Trial Ephemeral Template into the cluster.
oc create -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.0.GA/templates/rhpam79-trial-ephemeral.yaml -n openshift

# PAMをインストールするプロジェクトの作成
## Check if project exists
oc get project ${OCP_PROJECT}
## Create projects
oc new-project ${OCP_PROJECT} --display-name="RHPAM 7.9.0 - ${USER}" --description="RHPAM 7.9 for ${USER}."
## Annotate project namespace
oc annotate namespace ${OCP_PROJECT} openshift.io/requester=${USER} --overwrite
## Make user admin
oc policy add-role-to-user admin ${USER} -n ${OCP_PROJECT}

# PAMのインストール
## Check Secrets Business Central
oc get secret/businesscentral-app-secret -n ${OCP_PROJECT}
## Create Secrets Business Central
oc process -f ${PAM_SECRETS_TEMPLATE_YML} -p SECRET_NAME=businesscentral-app-secret | oc create -f - -n ${OCP_PROJECT}
## Check Secrets KIE-Server
oc get secret/kieserver-app-secret -n ${OCP_PROJECT}
## Create Secrets KIE-server
oc process -f ${PAM_SECRETS_TEMPLATE_YML} -p SECRET_NAME=kieserver-app-secret | oc create -f - -n ${OCP_PROJECT}
## Check Generic Secret with RHPAM Credentials
oc get secret/rhpam-credentials -n ${OCP_PROJECT}
## Create Generic Secret with RHPAM Credentials
oc create secret generic rhpam-credentials --from-literal=KIE_ADMIN_USER=pamAdmin --from-literal=KIE_ADMIN_PWD=redhatpam1! -n ${OCP_PROJECT}
## Create PAM7 environment
oc new-app --template=rhpam79-authoring -p APPLICATION_NAME=${APP_NAME} -p BUSINESS_CENTRAL_MEMORY_LIMIT="6Gi" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials' -p IMAGE_STREAM_NAMESPACE=openshift -n ${OCP_PROJECT}

# Business Centralのデプロイメントコンフィグ
## Configure Liveness probe
oc set probe dc/rhpam7-rhpamcentr --liveness --initial-delay-seconds=360 -n ${OCP_PROJECT}
## Configure Readiness probe
oc set probe dc/rhpam7-rhpamcentr --readiness --initial-delay-seconds=90 -n ${OCP_PROJECT}
## Set KIE_ADMIN Password
oc set env dc/rhpam7-rhpamcentr KIE_ADMIN_PWD=redhatpam1! -n ${OCP_PROJECT}
## Set KIE_SERVER_CONTROLLER Password
oc set env dc/rhpam7-rhpamcentr KIE_SERVER_CONTROLLER_PWD=test1234! -n ${OCP_PROJECT}
## Set KIE_SERVER Password
oc set env dc/rhpam7-rhpamcentr KIE_SERVER_PWD=test1234! -n ${OCP_PROJECT}

# Business Central のイメージストリーム
## Check if ImageStream exists
oc get is/rhpam-businesscentral-rhel8-cm-showcase -n ${OCP_PROJECT}
## Create ImageStream
oc create -f /Users/kamori/VSCode/WorkSpace/RHPAM_DM_Workshop/jp-localization/rhpam-rhdm-workshop-v1-infra-jp/apb/roles/rhpam_bc_cm_showcase/files/rhpam79-bc-cm-image-streams.yml -n ${OCP_PROJECT}
## Configure Business Central ImageStream
oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{"op": "replace", "path": "/spec/triggers/0/imageChangeParams/from/name", "value": "rhpam-businesscentral-rhel8-cm-showcase:7.9.0"}]' -n ${OCP_PROJECT}
## Configure Business Central ImageStream Namespace
oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{"op": "replace", "path": "/spec/triggers/0/imageChangeParams/from/namespace", "value": "rhpam-test"}]' -n ${OCP_PROJECT}
## Configure Business Central environment variables
oc set env dc/rhpam7-rhpamcentr JAVA_OPTS_APPEND="-Dorg.jbpm.casemgmt.showcase.url=/rhpam-case-mgmt-showcase -Dorg.kie.server.location=http://rhpam7-kieserver:8080/services/rest/server -Dorg.jbpm.wb.forms.renderer.ext=true" -n ${OCP_PROJECT}

# Kie-Server
## Check if ImageStream exists
oc get is/rhpam-kieserver-rhel8-cors -n ${OCP_PROJECT}
## Create ImageStream
oc create -f /Users/kamori/VSCode/WorkSpace/RHPAM_DM_Workshop/jp-localization/rhpam-rhdm-workshop-v1-infra-jp/apb/roles/rhpam_ks_cors/files/rhpam79-ks-cors-image-streams.yml -n ${OCP_PROJECT}
## Configure KIE-Server ImageStream
oc patch dc/rhpam7-kieserver --type='json' -p '[{"op": "replace", "path": "/spec/triggers/0/imageChangeParams/from/name", "value": "rhpam-kieserver-rhel8-cors:7.9.0"}]' -n ${OCP_PROJECT}
## Configure KIE-Server ImageStream Namespace
oc patch dc/rhpam7-kieserver --type='json' -p '[{"op": "replace", "path": "/spec/triggers/0/imageChangeParams/from/namespace", "value": "rhpam-test"}]' -n ${OCP_PROJECT}
## Configure KIE-Server Property for REST Calls
oc set env dc/rhpam7-kieserver DROOLS_SERVER_FILTER_CLASSES=false -n ${OCP_PROJECT}