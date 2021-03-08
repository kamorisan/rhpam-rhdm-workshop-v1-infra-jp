# ここから

kamori@kamori-mac ~ % oc logs -f apb
ansible-playbook 2.5.9
  config file = /opt/apb/ansible.cfg
  configured module search path = [u'/opt/apb/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible-playbook
  python version = 2.7.5 (default, Apr 11 2018, 07:36:10) [GCC 4.8.5 20150623 (Red Hat 4.8.5-28)]
Using /opt/apb/ansible.cfg as config file
Parsed /opt/apb/hosts inventory source with ini plugin
statically imported: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml
statically imported: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml
statically imported: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml
statically imported: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml

# provision.yml スタート
PLAYBOOK: provision.yml ********************************************************
1 plays in /opt/apb/actions/provision.yml

PLAY [rhpam-rhdm-workshopv2-apb playbook to provision the application] *********
META: ran handlers

# https://github.com/ansible/ansible-kubernetes-modules
TASK [ansible.kubernetes-modules : Install latest openshift client] ************
task path: /etc/ansible/roles/ansible.kubernetes-modules/tasks/main.yml:4
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

# https://github.com/ansibleplaybookbundle/ansible-asb-modules
TASK [ansibleplaybookbundle.asb-modules : debug] *******************************
task path: /etc/ansible/roles/ansibleplaybookbundle.asb-modules/tasks/main.yml:2
ok: [localhost] => {
    "msg": "Ansible Service Broker modules loaded"
}

# OPENSHIFT へのログイン login as super user with token
TASK [login as super user with token] ******************************************
task path: /opt/apb/actions/provision.yml:25
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166116.05-210517012295843 `" && echo ansible-tmp-1615166116.05-210517012295843="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166116.05-210517012295843 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpi2zf3V TO /opt/apb/.ansible/tmp/ansible-tmp-1615166116.05-210517012295843/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166116.05-210517012295843/ /opt/apb/.ansible/tmp/ansible-tmp-1615166116.05-210517012295843/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166116.05-210517012295843/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166116.05-210517012295843/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc login kubernetes.default --token=sha256~qT7dSlYjiJKxb5LRqNpqteVma24-9iofvqJnlpR4A2c --insecure-skip-tls-verify=true", 
    "delta": "0:00:00.792071", 
    "end": "2021-03-08 01:15:17.116792", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc login kubernetes.default --token=sha256~qT7dSlYjiJKxb5LRqNpqteVma24-9iofvqJnlpR4A2c --insecure-skip-tls-verify=true", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:16.324721", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "Logged into \"https://kubernetes.default:443\" as \"opentlc-mgr\" using the token provided.\n\nYou have access to 60 projects, the list has been suppressed. You can list all projects with 'oc projects'\n\nUsing project \"labs-infra\".", 
    "stdout_lines": [
        "Logged into \"https://kubernetes.default:443\" as \"opentlc-mgr\" using the token provided.", 
        "", 
        "You have access to 60 projects, the list has been suppressed. You can list all projects with 'oc projects'", 
        "", 
        "Using project \"labs-infra\"."
    ]
}

# OPENSHIFT へのユーザー名とパスワードを使ったログイン login as super user with pwd
TASK [login as super user with pwd] ********************************************
task path: /opt/apb/actions/provision.yml:33
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

# Extract the app route suffix
## Create an OpenShift Service
TASK [Create an OpenShift Service] *********************************************
task path: /opt/apb/actions/provision.yml:43
Using module file /usr/lib/python2.7/site-packages/ansible/modules/clustering/openshift/openshift_raw.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166117.64-13436904117336 `" && echo ansible-tmp-1615166117.64-13436904117336="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166117.64-13436904117336 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp0ojCdW TO /opt/apb/.ansible/tmp/ansible-tmp-1615166117.64-13436904117336/openshift_raw.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166117.64-13436904117336/ /opt/apb/.ansible/tmp/ansible-tmp-1615166117.64-13436904117336/openshift_raw.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166117.64-13436904117336/openshift_raw.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166117.64-13436904117336/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "invocation": {
        "module_args": {
            "api_key": null, 
            "cert_file": null, 
            "context": null, 
            "description": null, 
            "display_name": null, 
            "host": null, 
            "key_file": null, 
            "kubeconfig": null, 
            "name": "dummy", 
            "namespace": "labs-infra", 
            "password": null, 
            "spec_ports": [
                {
                    "name": "dummy-port", 
                    "port": 8080, 
                    "protocol": "TCP", 
                    "targetPort": 8080
                }
            ], 
            "ssl_ca_cert": null, 
            "username": null, 
            "verify_ssl": null
        }
    }, 
    "result": {
        "api_version": "v1", 
        "kind": "Service", 
        "metadata": {
            "annotations": null, 
            "cluster_name": null, 
            "creation_timestamp": "2021-03-08T01:15:19+00:00", 
            "deletion_grace_period_seconds": null, 
            "deletion_timestamp": null, 
            "finalizers": null, 
            "generate_name": null, 
            "generation": null, 
            "initializers": null, 
            "labels": null, 
            "name": "dummy", 
            "namespace": "labs-infra", 
            "owner_references": null, 
            "resource_version": "58784", 
            "self_link": "/api/v1/namespaces/labs-infra/services/dummy", 
            "uid": "4e6f9db7-20b4-426e-a6cb-5e47f227662f"
        }, 
        "spec": {
            "cluster_ip": "172.30.215.68", 
            "external_i_ps": null, 
            "external_name": null, 
            "external_traffic_policy": null, 
            "health_check_node_port": null, 
            "load_balancer_ip": null, 
            "load_balancer_source_ranges": null, 
            "ports": [
                {
                    "name": "dummy-port", 
                    "node_port": null, 
                    "port": 8080, 
                    "protocol": "TCP", 
                    "target_port": 8080
                }
            ], 
            "publish_not_ready_addresses": null, 
            "selector": null, 
            "session_affinity": "None", 
            "session_affinity_config": null, 
            "type": "ClusterIP"
        }, 
        "status": {
            "load_balancer": {
                "ingress": null
            }
        }
    }
}

## Wait for Service to be created (10秒待機)
TASK [Wait for Service to be created] ******************************************
task path: /opt/apb/actions/provision.yml:58
Pausing for 10 seconds
(ctrl+C then 'C' = continue early, ctrl+C then 'A' = abort)
ok: [localhost] => {
    "changed": false, 
    "delta": 10, 
    "echo": true, 
    "rc": 0, 
    "start": "2021-03-08 01:15:19.330027", 
    "stderr": "", 
    "stdout": "Paused for 10.0 seconds", 
    "stop": "2021-03-08 01:15:29.330131", 
    "user_input": ""
}

## Create an OpenShift Route (DUMMYのRouteを作成？)
TASK [Create an OpenShift Route] ***********************************************
task path: /opt/apb/actions/provision.yml:61
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166129.41-124428043459846 `" && echo ansible-tmp-1615166129.41-124428043459846="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166129.41-124428043459846 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpOeYiSX TO /opt/apb/.ansible/tmp/ansible-tmp-1615166129.41-124428043459846/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166129.41-124428043459846/ /opt/apb/.ansible/tmp/ansible-tmp-1615166129.41-124428043459846/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166129.41-124428043459846/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166129.41-124428043459846/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc expose service dummy -n labs-infra", 
    "delta": "0:00:01.354676", 
    "end": "2021-03-08 01:15:30.995079", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc expose service dummy -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:29.640403", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "route \"dummy\" exposed", 
    "stdout_lines": [
        "route \"dummy\" exposed"
    ]
}

## Get OpenShif Route url
TASK [Get OpenShif Route url] **************************************************
task path: /opt/apb/actions/provision.yml:63
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166131.04-46686102744865 `" && echo ansible-tmp-1615166131.04-46686102744865="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166131.04-46686102744865 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpJZXLDz TO /opt/apb/.ansible/tmp/ansible-tmp-1615166131.04-46686102744865/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166131.04-46686102744865/ /opt/apb/.ansible/tmp/ansible-tmp-1615166131.04-46686102744865/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166131.04-46686102744865/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166131.04-46686102744865/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get route dummy | awk 'FNR > 1 {print $2}'", 
    "delta": "0:00:00.750886", 
    "end": "2021-03-08 01:15:32.069414", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get route dummy | awk 'FNR > 1 {print $2}'", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:31.318528", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "dummy-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com", 
    "stdout_lines": [
        "dummy-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com"
    ]
}

## Set App Hostname suffix (Openshift API for command line 'oc' client の取得)
TASK [Set App Hostname suffix] *************************************************
task path: /opt/apb/actions/provision.yml:66
ok: [localhost] => {
    "ansible_facts": {
        "apps_hostname_suffix": "apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "changed": false
}

## Debug apps hostname suffix
TASK [Debug apps hostname suffix] **********************************************
task path: /opt/apb/actions/provision.yml:69
ok: [localhost] => {
    "msg": "App hostname suffix: apps.cluster-4b1a.4b1a.example.opentlc.com"
}

## Delete an OpenShift Service
TASK [Delete an OpenShift Service] *********************************************
task path: /opt/apb/actions/provision.yml:72
Using module file /usr/lib/python2.7/site-packages/ansible/modules/clustering/openshift/openshift_raw.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166132.41-262734154461022 `" && echo ansible-tmp-1615166132.41-262734154461022="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166132.41-262734154461022 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp6okqkQ TO /opt/apb/.ansible/tmp/ansible-tmp-1615166132.41-262734154461022/openshift_raw.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166132.41-262734154461022/ /opt/apb/.ansible/tmp/ansible-tmp-1615166132.41-262734154461022/openshift_raw.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166132.41-262734154461022/openshift_raw.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166132.41-262734154461022/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "invocation": {
        "module_args": {
            "api_key": null, 
            "cert_file": null, 
            "context": null, 
            "description": null, 
            "display_name": null, 
            "host": null, 
            "key_file": null, 
            "kubeconfig": null, 
            "name": "dummy", 
            "namespace": "labs-infra", 
            "password": null, 
            "ssl_ca_cert": null, 
            "username": null, 
            "verify_ssl": null
        }
    }, 
    "result": {}
}

## Wait for Service to be deleted (4秒待機)
TASK [Wait for Service to be deleted] ******************************************
task path: /opt/apb/actions/provision.yml:81
Pausing for 4 seconds
(ctrl+C then 'C' = continue early, ctrl+C then 'A' = abort)
ok: [localhost] => {
    "changed": false, 
    "delta": 4, 
    "echo": true, 
    "rc": 0, 
    "start": "2021-03-08 01:15:33.838055", 
    "stderr": "", 
    "stdout": "Paused for 4.0 seconds", 
    "stop": "2021-03-08 01:15:37.838180", 
    "user_input": ""
}

## Delete an OpenShift Route
TASK [Delete an OpenShift Route] ***********************************************
task path: /opt/apb/actions/provision.yml:84
Using module file /usr/lib/python2.7/site-packages/ansible/modules/clustering/openshift/openshift_raw.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166137.92-228865933286559 `" && echo ansible-tmp-1615166137.92-228865933286559="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166137.92-228865933286559 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpuuHyQQ TO /opt/apb/.ansible/tmp/ansible-tmp-1615166137.92-228865933286559/openshift_raw.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166137.92-228865933286559/ /opt/apb/.ansible/tmp/ansible-tmp-1615166137.92-228865933286559/openshift_raw.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166137.92-228865933286559/openshift_raw.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166137.92-228865933286559/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "invocation": {
        "module_args": {
            "api_key": null, 
            "cert_file": null, 
            "context": null, 
            "description": null, 
            "display_name": null, 
            "host": null, 
            "key_file": null, 
            "kubeconfig": null, 
            "name": "dummy", 
            "namespace": "labs-infra", 
            "password": null, 
            "ssl_ca_cert": null, 
            "username": null, 
            "verify_ssl": null
        }
    }, 
    "result": {}
}

# delete project quota
TASK [delete project quota] ****************************************************
task path: /opt/apb/actions/provision.yml:94
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166139.44-53502957640394 `" && echo ansible-tmp-1615166139.44-53502957640394="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166139.44-53502957640394 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpWDtTO7 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166139.44-53502957640394/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166139.44-53502957640394/ /opt/apb/.ansible/tmp/ansible-tmp-1615166139.44-53502957640394/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166139.44-53502957640394/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166139.44-53502957640394/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc delete limitrange --all -n labs-infra", 
    "delta": "0:00:00.759282", 
    "end": "2021-03-08 01:15:40.477059", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc delete limitrange --all -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:39.717777", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "limitrange \"labs-infra-core-resource-limits\" deleted", 
    "stdout_lines": [
        "limitrange \"labs-infra-core-resource-limits\" deleted"
    ]
}



# openshift_workshopper (ここからガイドのインストール)
# https://github.com/siamaksade/ansible-openshift-workshopper
## openshift_workshopper : check if workshopper project labs-infra exists
TASK [openshift_workshopper : check if workshopper project labs-infra exists] ***
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:5
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166140.54-119231020635651 `" && echo ansible-tmp-1615166140.54-119231020635651="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166140.54-119231020635651 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpe7z8m_ TO /opt/apb/.ansible/tmp/ansible-tmp-1615166140.54-119231020635651/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166140.54-119231020635651/ /opt/apb/.ansible/tmp/ansible-tmp-1615166140.54-119231020635651/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166140.54-119231020635651/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166140.54-119231020635651/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "cmd": "oc get project labs-infra", 
    "delta": "0:00:00.778279", 
    "end": "2021-03-08 01:15:41.603776", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:40.825497", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME         DISPLAY NAME   STATUS\nlabs-infra                  Active", 
    "stdout_lines": [
        "NAME         DISPLAY NAME   STATUS", 
        "labs-infra                  Active"
    ]
}

TASK [openshift_workshopper : create workshopper project labs-infra] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:11
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : assign user as project admin] ********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:15
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : annotate workshopper project labs-infra] *********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:24
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : check if workshopper guides-m1 exists] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:34
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166141.84-139651688661028 `" && echo ansible-tmp-1615166141.84-139651688661028="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166141.84-139651688661028 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpgwXaWt TO /opt/apb/.ansible/tmp/ansible-tmp-1615166141.84-139651688661028/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166141.84-139651688661028/ /opt/apb/.ansible/tmp/ansible-tmp-1615166141.84-139651688661028/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166141.84-139651688661028/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166141.84-139651688661028/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get service guides-m1 -n labs-infra", 
    "delta": "0:00:00.734096", 
    "end": "2021-03-08 01:15:42.855998", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get service guides-m1 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:15:42.121902", 
    "stderr": "Error from server (NotFound): services \"guides-m1\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): services \"guides-m1\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [openshift_workshopper : deploy workshopper] ******************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:4
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166143.0-42079626980933 `" && echo ansible-tmp-1615166143.0-42079626980933="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166143.0-42079626980933 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpBSbGMs TO /opt/apb/.ansible/tmp/ansible-tmp-1615166143.0-42079626980933/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166143.0-42079626980933/ /opt/apb/.ansible/tmp/ansible-tmp-1615166143.0-42079626980933/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166143.0-42079626980933/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166143.0-42079626980933/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --name=guides-m1 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m1-guides-jp/main/_rhpam-rhdm-workshop-module1.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m1-guides-jp/main -n labs-infra\n oc expose svc/guides-m1 -n labs-infra", 
    "delta": "0:00:07.225262", 
    "end": "2021-03-08 01:15:50.453259", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --name=guides-m1 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m1-guides-jp/main/_rhpam-rhdm-workshop-module1.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m1-guides-jp/main -n labs-infra\n oc expose svc/guides-m1 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:43.227997", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"\n\n    * An image stream will be created as \"guides-m1:latest\" that will track this image\n    * This image will be deployed in deployment config \"guides-m1\"\n    * Port 8080/tcp will be load balanced by service \"guides-m1\"\n      * Other containers can access this service through the hostname \"guides-m1\"\n\n--> Creating resources ...\n    imagestream \"guides-m1\" created\n    deploymentconfig \"guides-m1\" created\n    service \"guides-m1\" created\n--> Success\n    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:\n     'oc expose svc/guides-m1' \n    Run 'oc status' to view your app.\nroute \"guides-m1\" exposed", 
    "stdout_lines": [
        "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"", 
        "", 
        "    * An image stream will be created as \"guides-m1:latest\" that will track this image", 
        "    * This image will be deployed in deployment config \"guides-m1\"", 
        "    * Port 8080/tcp will be load balanced by service \"guides-m1\"", 
        "      * Other containers can access this service through the hostname \"guides-m1\"", 
        "", 
        "--> Creating resources ...", 
        "    imagestream \"guides-m1\" created", 
        "    deploymentconfig \"guides-m1\" created", 
        "    service \"guides-m1\" created", 
        "--> Success", 
        "    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:", 
        "     'oc expose svc/guides-m1' ", 
        "    Run 'oc status' to view your app.", 
        "route \"guides-m1\" exposed"
    ]
}

TASK [openshift_workshopper : set workshopper resources] ***********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:12
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166150.61-278534017086655 `" && echo ansible-tmp-1615166150.61-278534017086655="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166150.61-278534017086655 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpg6ua9s TO /opt/apb/.ansible/tmp/ansible-tmp-1615166150.61-278534017086655/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166150.61-278534017086655/ /opt/apb/.ansible/tmp/ansible-tmp-1615166150.61-278534017086655/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166150.61-278534017086655/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166150.61-278534017086655/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set resources dc/guides-m1 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
    "delta": "0:00:00.822864", 
    "end": "2021-03-08 01:15:51.652716", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set resources dc/guides-m1 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:50.829852", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m1\" resource requirements updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m1\" resource requirements updated"
    ]
}

TASK [openshift_workshopper : configure workshopper guide env vars] ************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:15
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166151.74-252944569203983 `" && echo ansible-tmp-1615166151.74-252944569203983="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166151.74-252944569203983 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpdL9BWw TO /opt/apb/.ansible/tmp/ansible-tmp-1615166151.74-252944569203983/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166151.74-252944569203983/ /opt/apb/.ansible/tmp/ansible-tmp-1615166151.74-252944569203983/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166151.74-252944569203983/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166151.74-252944569203983/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com', 'key': u'OPENSHIFT_CONSOLE_URL'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m1 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
    "delta": "0:00:00.789889", 
    "end": "2021-03-08 01:15:52.804096", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m1 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "OPENSHIFT_CONSOLE_URL", 
        "value": "https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:52.014207", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m1\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m1\" updated"
    ]
}
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166152.9-195902623456948 `" && echo ansible-tmp-1615166152.9-195902623456948="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166152.9-195902623456948 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpaSRikw TO /opt/apb/.ansible/tmp/ansible-tmp-1615166152.9-195902623456948/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166152.9-195902623456948/ /opt/apb/.ansible/tmp/ansible-tmp-1615166152.9-195902623456948/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166152.9-195902623456948/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166152.9-195902623456948/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com', 'key': u'NEXUS_URL'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m1 NEXUS_URL=http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
    "delta": "0:00:00.787922", 
    "end": "2021-03-08 01:15:53.918647", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m1 NEXUS_URL=http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "NEXUS_URL", 
        "value": "http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:53.130725", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m1\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m1\" updated"
    ]
}
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166154.02-239573018336382 `" && echo ansible-tmp-1615166154.02-239573018336382="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166154.02-239573018336382 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmplOD4Jc TO /opt/apb/.ansible/tmp/ansible-tmp-1615166154.02-239573018336382/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166154.02-239573018336382/ /opt/apb/.ansible/tmp/ansible-tmp-1615166154.02-239573018336382/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166154.02-239573018336382/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166154.02-239573018336382/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'-XX', 'key': u'PROJECT_SUFFIX'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m1 PROJECT_SUFFIX=-XX -n labs-infra", 
    "delta": "0:00:00.767872", 
    "end": "2021-03-08 01:15:55.072174", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m1 PROJECT_SUFFIX=-XX -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "PROJECT_SUFFIX", 
        "value": "-XX"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:54.304302", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m1\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m1\" updated"
    ]
}

TASK [openshift_workshopper : set workshopper probes] **************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:19
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166155.2-88544954442238 `" && echo ansible-tmp-1615166155.2-88544954442238="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166155.2-88544954442238 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpfU9ZRI TO /opt/apb/.ansible/tmp/ansible-tmp-1615166155.2-88544954442238/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166155.2-88544954442238/ /opt/apb/.ansible/tmp/ansible-tmp-1615166155.2-88544954442238/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166155.2-88544954442238/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166155.2-88544954442238/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/guides-m1 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
    "delta": "0:00:00.834809", 
    "end": "2021-03-08 01:15:56.265241", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/guides-m1 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:55.430432", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m1\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m1\" updated"
    ]
}

TASK [openshift_workshopper : check if workshopper project labs-infra exists] ***
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:5
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166156.32-6866261797681 `" && echo ansible-tmp-1615166156.32-6866261797681="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166156.32-6866261797681 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpNksvhc TO /opt/apb/.ansible/tmp/ansible-tmp-1615166156.32-6866261797681/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166156.32-6866261797681/ /opt/apb/.ansible/tmp/ansible-tmp-1615166156.32-6866261797681/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166156.32-6866261797681/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166156.32-6866261797681/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "cmd": "oc get project labs-infra", 
    "delta": "0:00:00.815451", 
    "end": "2021-03-08 01:15:57.442235", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:56.626784", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME         DISPLAY NAME   STATUS\nlabs-infra                  Active", 
    "stdout_lines": [
        "NAME         DISPLAY NAME   STATUS", 
        "labs-infra                  Active"
    ]
}

TASK [openshift_workshopper : create workshopper project labs-infra] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:11
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : assign user as project admin] ********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:15
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : annotate workshopper project labs-infra] *********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:24
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : check if workshopper guides-m2 exists] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:34
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166157.71-278927323627602 `" && echo ansible-tmp-1615166157.71-278927323627602="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166157.71-278927323627602 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp_13nSj TO /opt/apb/.ansible/tmp/ansible-tmp-1615166157.71-278927323627602/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166157.71-278927323627602/ /opt/apb/.ansible/tmp/ansible-tmp-1615166157.71-278927323627602/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166157.71-278927323627602/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166157.71-278927323627602/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get service guides-m2 -n labs-infra", 
    "delta": "0:00:00.806504", 
    "end": "2021-03-08 01:15:58.745223", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get service guides-m2 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:15:57.938719", 
    "stderr": "Error from server (NotFound): services \"guides-m2\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): services \"guides-m2\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [openshift_workshopper : deploy workshopper] ******************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:4
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166158.84-131655028186322 `" && echo ansible-tmp-1615166158.84-131655028186322="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166158.84-131655028186322 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp2o6Z1h TO /opt/apb/.ansible/tmp/ansible-tmp-1615166158.84-131655028186322/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166158.84-131655028186322/ /opt/apb/.ansible/tmp/ansible-tmp-1615166158.84-131655028186322/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166158.84-131655028186322/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166158.84-131655028186322/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --name=guides-m2 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m2-guides-jp/main/_rhpam-rhdm-workshop-module2.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m2-guides-jp/main -n labs-infra\n oc expose svc/guides-m2 -n labs-infra", 
    "delta": "0:00:02.424932", 
    "end": "2021-03-08 01:16:01.545931", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --name=guides-m2 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m2-guides-jp/main/_rhpam-rhdm-workshop-module2.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m2-guides-jp/main -n labs-infra\n oc expose svc/guides-m2 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:15:59.120999", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"\n\n    * An image stream will be created as \"guides-m2:latest\" that will track this image\n    * This image will be deployed in deployment config \"guides-m2\"\n    * Port 8080/tcp will be load balanced by service \"guides-m2\"\n      * Other containers can access this service through the hostname \"guides-m2\"\n\n--> Creating resources ...\n    imagestream \"guides-m2\" created\n    deploymentconfig \"guides-m2\" created\n    service \"guides-m2\" created\n--> Success\n    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:\n     'oc expose svc/guides-m2' \n    Run 'oc status' to view your app.\nroute \"guides-m2\" exposed", 
    "stdout_lines": [
        "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"", 
        "", 
        "    * An image stream will be created as \"guides-m2:latest\" that will track this image", 
        "    * This image will be deployed in deployment config \"guides-m2\"", 
        "    * Port 8080/tcp will be load balanced by service \"guides-m2\"", 
        "      * Other containers can access this service through the hostname \"guides-m2\"", 
        "", 
        "--> Creating resources ...", 
        "    imagestream \"guides-m2\" created", 
        "    deploymentconfig \"guides-m2\" created", 
        "    service \"guides-m2\" created", 
        "--> Success", 
        "    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:", 
        "     'oc expose svc/guides-m2' ", 
        "    Run 'oc status' to view your app.", 
        "route \"guides-m2\" exposed"
    ]
}

TASK [openshift_workshopper : set workshopper resources] ***********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:12
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166161.63-281096793634648 `" && echo ansible-tmp-1615166161.63-281096793634648="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166161.63-281096793634648 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpXBCXRN TO /opt/apb/.ansible/tmp/ansible-tmp-1615166161.63-281096793634648/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166161.63-281096793634648/ /opt/apb/.ansible/tmp/ansible-tmp-1615166161.63-281096793634648/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166161.63-281096793634648/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166161.63-281096793634648/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set resources dc/guides-m2 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
    "delta": "0:00:00.766518", 
    "end": "2021-03-08 01:16:02.675613", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set resources dc/guides-m2 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:01.909095", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m2\" resource requirements updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m2\" resource requirements updated"
    ]
}

TASK [openshift_workshopper : configure workshopper guide env vars] ************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:15
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166162.81-270765244209142 `" && echo ansible-tmp-1615166162.81-270765244209142="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166162.81-270765244209142 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpQPjWcU TO /opt/apb/.ansible/tmp/ansible-tmp-1615166162.81-270765244209142/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166162.81-270765244209142/ /opt/apb/.ansible/tmp/ansible-tmp-1615166162.81-270765244209142/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166162.81-270765244209142/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166162.81-270765244209142/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com', 'key': u'OPENSHIFT_CONSOLE_URL'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m2 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
    "delta": "0:00:00.811664", 
    "end": "2021-03-08 01:16:03.850583", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m2 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "OPENSHIFT_CONSOLE_URL", 
        "value": "https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:03.038919", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m2\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m2\" updated"
    ]
}
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166163.91-80779217522428 `" && echo ansible-tmp-1615166163.91-80779217522428="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166163.91-80779217522428 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmptJJZMs TO /opt/apb/.ansible/tmp/ansible-tmp-1615166163.91-80779217522428/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166163.91-80779217522428/ /opt/apb/.ansible/tmp/ansible-tmp-1615166163.91-80779217522428/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166163.91-80779217522428/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166163.91-80779217522428/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com', 'key': u'NEXUS_URL'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m2 NEXUS_URL=http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
    "delta": "0:00:00.890695", 
    "end": "2021-03-08 01:16:05.032475", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m2 NEXUS_URL=http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "NEXUS_URL", 
        "value": "http://nexus-labs-infra.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:04.141780", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m2\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m2\" updated"
    ]
}
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166165.11-201182714474836 `" && echo ansible-tmp-1615166165.11-201182714474836="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166165.11-201182714474836 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpI8_K9Q TO /opt/apb/.ansible/tmp/ansible-tmp-1615166165.11-201182714474836/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166165.11-201182714474836/ /opt/apb/.ansible/tmp/ansible-tmp-1615166165.11-201182714474836/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166165.11-201182714474836/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166165.11-201182714474836/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'-XX', 'key': u'PROJECT_SUFFIX'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m2 PROJECT_SUFFIX=-XX -n labs-infra", 
    "delta": "0:00:00.806335", 
    "end": "2021-03-08 01:16:06.139971", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m2 PROJECT_SUFFIX=-XX -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "PROJECT_SUFFIX", 
        "value": "-XX"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:05.333636", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m2\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m2\" updated"
    ]
}

TASK [openshift_workshopper : set workshopper probes] **************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:19
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166166.22-66463681804000 `" && echo ansible-tmp-1615166166.22-66463681804000="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166166.22-66463681804000 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpsNYdVq TO /opt/apb/.ansible/tmp/ansible-tmp-1615166166.22-66463681804000/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166166.22-66463681804000/ /opt/apb/.ansible/tmp/ansible-tmp-1615166166.22-66463681804000/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166166.22-66463681804000/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166166.22-66463681804000/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/guides-m2 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
    "delta": "0:00:00.763752", 
    "end": "2021-03-08 01:16:07.267085", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/guides-m2 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:06.503333", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m2\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m2\" updated"
    ]
}

TASK [openshift_workshopper : check if workshopper project labs-infra exists] ***
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:5
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166167.34-87484720337244 `" && echo ansible-tmp-1615166167.34-87484720337244="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166167.34-87484720337244 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpTDX_6A TO /opt/apb/.ansible/tmp/ansible-tmp-1615166167.34-87484720337244/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166167.34-87484720337244/ /opt/apb/.ansible/tmp/ansible-tmp-1615166167.34-87484720337244/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166167.34-87484720337244/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166167.34-87484720337244/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "cmd": "oc get project labs-infra", 
    "delta": "0:00:00.777518", 
    "end": "2021-03-08 01:16:08.401059", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:07.623541", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME         DISPLAY NAME   STATUS\nlabs-infra                  Active", 
    "stdout_lines": [
        "NAME         DISPLAY NAME   STATUS", 
        "labs-infra                  Active"
    ]
}

TASK [openshift_workshopper : create workshopper project labs-infra] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:11
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : assign user as project admin] ********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:15
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : annotate workshopper project labs-infra] *********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:24
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : check if workshopper guides-m3 exists] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:34
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166168.63-85055173480695 `" && echo ansible-tmp-1615166168.63-85055173480695="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166168.63-85055173480695 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpuy4HJd TO /opt/apb/.ansible/tmp/ansible-tmp-1615166168.63-85055173480695/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166168.63-85055173480695/ /opt/apb/.ansible/tmp/ansible-tmp-1615166168.63-85055173480695/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166168.63-85055173480695/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166168.63-85055173480695/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get service guides-m3 -n labs-infra", 
    "delta": "0:00:00.797020", 
    "end": "2021-03-08 01:16:09.646534", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get service guides-m3 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:16:08.849514", 
    "stderr": "Error from server (NotFound): services \"guides-m3\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): services \"guides-m3\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [openshift_workshopper : deploy workshopper] ******************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:4
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166169.75-219310876774011 `" && echo ansible-tmp-1615166169.75-219310876774011="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166169.75-219310876774011 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpRbrGbG TO /opt/apb/.ansible/tmp/ansible-tmp-1615166169.75-219310876774011/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166169.75-219310876774011/ /opt/apb/.ansible/tmp/ansible-tmp-1615166169.75-219310876774011/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166169.75-219310876774011/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166169.75-219310876774011/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --name=guides-m3 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m3-guides-jp/main/_rhpam-rhdm-workshop-module3.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m3-guides-jp/main -n labs-infra\n oc expose svc/guides-m3 -n labs-infra", 
    "delta": "0:00:02.277114", 
    "end": "2021-03-08 01:16:12.303377", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --name=guides-m3 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m3-guides-jp/main/_rhpam-rhdm-workshop-module3.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m3-guides-jp/main -n labs-infra\n oc expose svc/guides-m3 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:10.026263", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"\n\n    * An image stream will be created as \"guides-m3:latest\" that will track this image\n    * This image will be deployed in deployment config \"guides-m3\"\n    * Port 8080/tcp will be load balanced by service \"guides-m3\"\n      * Other containers can access this service through the hostname \"guides-m3\"\n\n--> Creating resources ...\n    imagestream \"guides-m3\" created\n    deploymentconfig \"guides-m3\" created\n    service \"guides-m3\" created\n--> Success\n    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:\n     'oc expose svc/guides-m3' \n    Run 'oc status' to view your app.\nroute \"guides-m3\" exposed", 
    "stdout_lines": [
        "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"", 
        "", 
        "    * An image stream will be created as \"guides-m3:latest\" that will track this image", 
        "    * This image will be deployed in deployment config \"guides-m3\"", 
        "    * Port 8080/tcp will be load balanced by service \"guides-m3\"", 
        "      * Other containers can access this service through the hostname \"guides-m3\"", 
        "", 
        "--> Creating resources ...", 
        "    imagestream \"guides-m3\" created", 
        "    deploymentconfig \"guides-m3\" created", 
        "    service \"guides-m3\" created", 
        "--> Success", 
        "    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:", 
        "     'oc expose svc/guides-m3' ", 
        "    Run 'oc status' to view your app.", 
        "route \"guides-m3\" exposed"
    ]
}

TASK [openshift_workshopper : set workshopper resources] ***********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:12
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166172.41-11511592692863 `" && echo ansible-tmp-1615166172.41-11511592692863="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166172.41-11511592692863 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpiaPtCi TO /opt/apb/.ansible/tmp/ansible-tmp-1615166172.41-11511592692863/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166172.41-11511592692863/ /opt/apb/.ansible/tmp/ansible-tmp-1615166172.41-11511592692863/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166172.41-11511592692863/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166172.41-11511592692863/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set resources dc/guides-m3 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
    "delta": "0:00:00.817102", 
    "end": "2021-03-08 01:16:13.460599", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set resources dc/guides-m3 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:12.643497", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m3\" resource requirements updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m3\" resource requirements updated"
    ]
}

TASK [openshift_workshopper : configure workshopper guide env vars] ************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:15
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166173.54-40932105180 `" && echo ansible-tmp-1615166173.54-40932105180="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166173.54-40932105180 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpXaiBgd TO /opt/apb/.ansible/tmp/ansible-tmp-1615166173.54-40932105180/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166173.54-40932105180/ /opt/apb/.ansible/tmp/ansible-tmp-1615166173.54-40932105180/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166173.54-40932105180/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166173.54-40932105180/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com', 'key': u'OPENSHIFT_CONSOLE_URL'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m3 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
    "delta": "0:00:00.802406", 
    "end": "2021-03-08 01:16:14.627048", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m3 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "OPENSHIFT_CONSOLE_URL", 
        "value": "https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:13.824642", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m3\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m3\" updated"
    ]
}
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166174.7-56973559417568 `" && echo ansible-tmp-1615166174.7-56973559417568="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166174.7-56973559417568 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpaDOqpU TO /opt/apb/.ansible/tmp/ansible-tmp-1615166174.7-56973559417568/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166174.7-56973559417568/ /opt/apb/.ansible/tmp/ansible-tmp-1615166174.7-56973559417568/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166174.7-56973559417568/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166174.7-56973559417568/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'-XX', 'key': u'PROJECT_SUFFIX'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m3 PROJECT_SUFFIX=-XX -n labs-infra", 
    "delta": "0:00:00.808691", 
    "end": "2021-03-08 01:16:15.739095", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m3 PROJECT_SUFFIX=-XX -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "PROJECT_SUFFIX", 
        "value": "-XX"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:14.930404", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m3\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m3\" updated"
    ]
}

TASK [openshift_workshopper : set workshopper probes] **************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:19
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166175.83-20458110606119 `" && echo ansible-tmp-1615166175.83-20458110606119="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166175.83-20458110606119 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpwGKzSW TO /opt/apb/.ansible/tmp/ansible-tmp-1615166175.83-20458110606119/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166175.83-20458110606119/ /opt/apb/.ansible/tmp/ansible-tmp-1615166175.83-20458110606119/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166175.83-20458110606119/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166175.83-20458110606119/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/guides-m3 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
    "delta": "0:00:00.758390", 
    "end": "2021-03-08 01:16:16.865808", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/guides-m3 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:16.107418", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m3\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m3\" updated"
    ]
}

TASK [openshift_workshopper : check if workshopper project labs-infra exists] ***
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:5
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166176.94-81239259183032 `" && echo ansible-tmp-1615166176.94-81239259183032="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166176.94-81239259183032 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpk0vF5p TO /opt/apb/.ansible/tmp/ansible-tmp-1615166176.94-81239259183032/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166176.94-81239259183032/ /opt/apb/.ansible/tmp/ansible-tmp-1615166176.94-81239259183032/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166176.94-81239259183032/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166176.94-81239259183032/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "cmd": "oc get project labs-infra", 
    "delta": "0:00:00.804993", 
    "end": "2021-03-08 01:16:18.046424", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:17.241431", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME         DISPLAY NAME   STATUS\nlabs-infra                  Active", 
    "stdout_lines": [
        "NAME         DISPLAY NAME   STATUS", 
        "labs-infra                  Active"
    ]
}

TASK [openshift_workshopper : create workshopper project labs-infra] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:11
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : assign user as project admin] ********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:15
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : annotate workshopper project labs-infra] *********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:24
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [openshift_workshopper : check if workshopper guides-m4 exists] ***********
task path: /etc/ansible/roles/openshift_workshopper/tasks/main.yml:34
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166178.34-138245884095404 `" && echo ansible-tmp-1615166178.34-138245884095404="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166178.34-138245884095404 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpL4qWtF TO /opt/apb/.ansible/tmp/ansible-tmp-1615166178.34-138245884095404/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166178.34-138245884095404/ /opt/apb/.ansible/tmp/ansible-tmp-1615166178.34-138245884095404/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166178.34-138245884095404/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166178.34-138245884095404/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get service guides-m4 -n labs-infra", 
    "delta": "0:00:00.736432", 
    "end": "2021-03-08 01:16:19.349264", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get service guides-m4 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:16:18.612832", 
    "stderr": "Error from server (NotFound): services \"guides-m4\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): services \"guides-m4\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [openshift_workshopper : deploy workshopper] ******************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:4
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166179.51-77296715883852 `" && echo ansible-tmp-1615166179.51-77296715883852="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166179.51-77296715883852 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp76MLwp TO /opt/apb/.ansible/tmp/ansible-tmp-1615166179.51-77296715883852/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166179.51-77296715883852/ /opt/apb/.ansible/tmp/ansible-tmp-1615166179.51-77296715883852/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166179.51-77296715883852/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166179.51-77296715883852/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --name=guides-m4 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m4-guides-jp/main/_rhpam-rhdm-workshop-module4.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m4-guides-jp/main -n labs-infra\n oc expose svc/guides-m4 -n labs-infra", 
    "delta": "0:00:02.385992", 
    "end": "2021-03-08 01:16:22.123492", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --name=guides-m4 --docker-image=quay.io/osevg/workshopper:latest -e WORKSHOPS_URLS=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m4-guides-jp/main/_rhpam-rhdm-workshop-module4.yml -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m4-guides-jp/main -n labs-infra\n oc expose svc/guides-m4 -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:19.737500", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"\n\n    * An image stream will be created as \"guides-m4:latest\" that will track this image\n    * This image will be deployed in deployment config \"guides-m4\"\n    * Port 8080/tcp will be load balanced by service \"guides-m4\"\n      * Other containers can access this service through the hostname \"guides-m4\"\n\n--> Creating resources ...\n    imagestream \"guides-m4\" created\n    deploymentconfig \"guides-m4\" created\n    service \"guides-m4\" created\n--> Success\n    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:\n     'oc expose svc/guides-m4' \n    Run 'oc status' to view your app.\nroute \"guides-m4\" exposed", 
    "stdout_lines": [
        "--> Found Docker image 82cc938 (2 years old) from quay.io for \"quay.io/osevg/workshopper:latest\"", 
        "", 
        "    * An image stream will be created as \"guides-m4:latest\" that will track this image", 
        "    * This image will be deployed in deployment config \"guides-m4\"", 
        "    * Port 8080/tcp will be load balanced by service \"guides-m4\"", 
        "      * Other containers can access this service through the hostname \"guides-m4\"", 
        "", 
        "--> Creating resources ...", 
        "    imagestream \"guides-m4\" created", 
        "    deploymentconfig \"guides-m4\" created", 
        "    service \"guides-m4\" created", 
        "--> Success", 
        "    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:", 
        "     'oc expose svc/guides-m4' ", 
        "    Run 'oc status' to view your app.", 
        "route \"guides-m4\" exposed"
    ]
}

TASK [openshift_workshopper : set workshopper resources] ***********************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:12
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166182.22-107830424081259 `" && echo ansible-tmp-1615166182.22-107830424081259="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166182.22-107830424081259 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpfy0UMA TO /opt/apb/.ansible/tmp/ansible-tmp-1615166182.22-107830424081259/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166182.22-107830424081259/ /opt/apb/.ansible/tmp/ansible-tmp-1615166182.22-107830424081259/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166182.22-107830424081259/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166182.22-107830424081259/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set resources dc/guides-m4 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
    "delta": "0:00:00.856983", 
    "end": "2021-03-08 01:16:23.303360", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set resources dc/guides-m4 --limits=cpu=0,memory=512Mi --requests=cpu=0,memory=128Mi -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:22.446377", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m4\" resource requirements updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m4\" resource requirements updated"
    ]
}

TASK [openshift_workshopper : configure workshopper guide env vars] ************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:15
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166183.43-55523799778187 `" && echo ansible-tmp-1615166183.43-55523799778187="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166183.43-55523799778187 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp6hfogF TO /opt/apb/.ansible/tmp/ansible-tmp-1615166183.43-55523799778187/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166183.43-55523799778187/ /opt/apb/.ansible/tmp/ansible-tmp-1615166183.43-55523799778187/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166183.43-55523799778187/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166183.43-55523799778187/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com', 'key': u'OPENSHIFT_CONSOLE_URL'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m4 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
    "delta": "0:00:00.796168", 
    "end": "2021-03-08 01:16:24.502111", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m4 OPENSHIFT_CONSOLE_URL=https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "OPENSHIFT_CONSOLE_URL", 
        "value": "https://console-openshift-console.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:23.705943", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m4\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m4\" updated"
    ]
}
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166184.55-240385582495522 `" && echo ansible-tmp-1615166184.55-240385582495522="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166184.55-240385582495522 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpgJykOr TO /opt/apb/.ansible/tmp/ansible-tmp-1615166184.55-240385582495522/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166184.55-240385582495522/ /opt/apb/.ansible/tmp/ansible-tmp-1615166184.55-240385582495522/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166184.55-240385582495522/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166184.55-240385582495522/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => (item={'value': u'-XX', 'key': u'PROJECT_SUFFIX'}) => {
    "changed": true, 
    "cmd": "oc set env dc/guides-m4 PROJECT_SUFFIX=-XX -n labs-infra", 
    "delta": "0:00:00.842331", 
    "end": "2021-03-08 01:16:25.672780", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/guides-m4 PROJECT_SUFFIX=-XX -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "item": {
        "key": "PROJECT_SUFFIX", 
        "value": "-XX"
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:24.830449", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m4\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m4\" updated"
    ]
}

TASK [openshift_workshopper : set workshopper probes] **************************
task path: /etc/ansible/roles/openshift_workshopper/tasks/deploy.yml:19
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166185.74-256424251651483 `" && echo ansible-tmp-1615166185.74-256424251651483="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166185.74-256424251651483 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpkeYs7Z TO /opt/apb/.ansible/tmp/ansible-tmp-1615166185.74-256424251651483/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166185.74-256424251651483/ /opt/apb/.ansible/tmp/ansible-tmp-1615166185.74-256424251651483/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166185.74-256424251651483/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166185.74-256424251651483/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/guides-m4 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
    "delta": "0:00:00.854928", 
    "end": "2021-03-08 01:16:26.869163", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/guides-m4 -n labs-infra --readiness --liveness --get-url=http://:8080/ --failure-threshold=5 --initial-delay-seconds=30", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:26.014235", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"guides-m4\" updated", 
    "stdout_lines": [
        "deploymentconfig \"guides-m4\" updated"
    ]
}

# ここまでガイドのインストール

# ここから Java のインストール？

# get openjdk image stream
TASK [get openjdk image stream] ************************************************
task path: /opt/apb/actions/provision.yml:163
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166186.94-240259993228876 `" && echo ansible-tmp-1615166186.94-240259993228876="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166186.94-240259993228876 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpNAzeWn TO /opt/apb/.ansible/tmp/ansible-tmp-1615166186.94-240259993228876/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166186.94-240259993228876/ /opt/apb/.ansible/tmp/ansible-tmp-1615166186.94-240259993228876/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166186.94-240259993228876/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166186.94-240259993228876/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get is java -n openshift", 
    "delta": "0:00:00.829711", 
    "end": "2021-03-08 01:16:28.046327", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is java -n openshift", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:27.216616", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME      DOCKER REPO                                                                                        TAGS                                  UPDATED\njava      default-route-openshift-image-registry.apps.cluster-4b1a.4b1a.example.opentlc.com/openshift/java   8,latest,openjdk-11-el7 + 4 more...   2 hours ago", 
    "stdout_lines": [
        "NAME      DOCKER REPO                                                                                        TAGS                                  UPDATED", 
        "java      default-route-openshift-image-registry.apps.cluster-4b1a.4b1a.example.opentlc.com/openshift/java   8,latest,openjdk-11-el7 + 4 more...   2 hours ago"
    ]
}

# install java image stream
TASK [install java image stream] ***********************************************
task path: /opt/apb/actions/provision.yml:169
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

# ここからPAMインストール - Install PAM templates

# Check if PAM ImageStreams exists PAMのイメージストリームのチェック
TASK [Check if PAM ImageStreams exists] ****************************************
task path: /opt/apb/actions/provision.yml:177
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166188.15-205015733215136 `" && echo ansible-tmp-1615166188.15-205015733215136="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166188.15-205015733215136 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpqoQl5f TO /opt/apb/.ansible/tmp/ansible-tmp-1615166188.15-205015733215136/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166188.15-205015733215136/ /opt/apb/.ansible/tmp/ansible-tmp-1615166188.15-205015733215136/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166188.15-205015733215136/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166188.15-205015733215136/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get is/rhpam-businesscentral-rhel8 -n openshift", 
    "delta": "0:00:00.813591", 
    "end": "2021-03-08 01:16:29.250961", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is/rhpam-businesscentral-rhel8 -n openshift", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:28.437370", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME                          DOCKER REPO                                                                                                               TAGS      UPDATED\nrhpam-businesscentral-rhel8   default-route-openshift-image-registry.apps.cluster-4b1a.4b1a.example.opentlc.com/openshift/rhpam-businesscentral-rhel8   7.8.0     2 hours ago", 
    "stdout_lines": [
        "NAME                          DOCKER REPO                                                                                                               TAGS      UPDATED", 
        "rhpam-businesscentral-rhel8   default-route-openshift-image-registry.apps.cluster-4b1a.4b1a.example.opentlc.com/openshift/rhpam-businesscentral-rhel8   7.8.0     2 hours ago"
    ]
}

# Import the RHPAM ImageStreams into the cluster. PAMのイメージストリームのチェック → なければインストール
TASK [Import the RHPAM ImageStreams into the cluster.] *************************
task path: /opt/apb/actions/provision.yml:183
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

# Check if RHPAM Authoring Template exists RHPAM Authoring Templateのチェック → なければインストール
TASK [Check if RHPAM Authoring Template exists] ********************************
task path: /opt/apb/actions/provision.yml:189
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166189.4-246160139769814 `" && echo ansible-tmp-1615166189.4-246160139769814="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166189.4-246160139769814 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpVEereO TO /opt/apb/.ansible/tmp/ansible-tmp-1615166189.4-246160139769814/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166189.4-246160139769814/ /opt/apb/.ansible/tmp/ansible-tmp-1615166189.4-246160139769814/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166189.4-246160139769814/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166189.4-246160139769814/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get template/rhpam79-authoring -n openshift", 
    "delta": "0:00:00.785915", 
    "end": "2021-03-08 01:16:30.421319", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get template/rhpam79-authoring -n openshift", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:29.635404", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME                DESCRIPTION                                                                        PARAMETERS      OBJECTS\nrhpam79-authoring   Application template for a non-HA persistent authoring environment, for Red H...   73 (45 blank)   12", 
    "stdout_lines": [
        "NAME                DESCRIPTION                                                                        PARAMETERS      OBJECTS", 
        "rhpam79-authoring   Application template for a non-HA persistent authoring environment, for Red H...   73 (45 blank)   12"
    ]
}

# Import the RHPAM Authoring Template into the cluster
TASK [Import the RHPAM Authoring Template into the cluster.] *******************
task path: /opt/apb/actions/provision.yml:195
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

# Check if RHPAM Trial Template exists RHPAM Trial Templateのチェック → なければインストール
TASK [Check if RHPAM Trial Template exists] ************************************
task path: /opt/apb/actions/provision.yml:201
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166190.53-62696899050417 `" && echo ansible-tmp-1615166190.53-62696899050417="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166190.53-62696899050417 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmplGu34m TO /opt/apb/.ansible/tmp/ansible-tmp-1615166190.53-62696899050417/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166190.53-62696899050417/ /opt/apb/.ansible/tmp/ansible-tmp-1615166190.53-62696899050417/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166190.53-62696899050417/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166190.53-62696899050417/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get template/rhpam79-trial-ephemeral -n openshift", 
    "delta": "0:00:00.767337", 
    "end": "2021-03-08 01:16:31.576581", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get template/rhpam79-trial-ephemeral -n openshift", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:30.809244", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME                      DESCRIPTION                                                                       PARAMETERS      OBJECTS\nrhpam79-trial-ephemeral   Application template for an ephemeral authoring and testing environment, for...   62 (39 blank)   8", 
    "stdout_lines": [
        "NAME                      DESCRIPTION                                                                       PARAMETERS      OBJECTS", 
        "rhpam79-trial-ephemeral   Application template for an ephemeral authoring and testing environment, for...   62 (39 blank)   8"
    ]
}

# Import the RHPAM Trial Ephemeral Template into the cluster
TASK [Import the RHPAM Trial Ephemeral Template into the cluster.] *************
task path: /opt/apb/actions/provision.yml:207
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

# Import Create React App template React App template のインストール
TASK [Import Create React App template] ****************************************
task path: /opt/apb/actions/provision.yml:213
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166191.72-176423716358007 `" && echo ansible-tmp-1615166191.72-176423716358007="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166191.72-176423716358007 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpwDFwbS TO /opt/apb/.ansible/tmp/ansible-tmp-1615166191.72-176423716358007/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166191.72-176423716358007/ /opt/apb/.ansible/tmp/ansible-tmp-1615166191.72-176423716358007/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166191.72-176423716358007/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166191.72-176423716358007/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create -f https://raw.githubusercontent.com/DuncanDoyle/reactjs-openshift/master/create-react-app-openshift-template.yaml -n openshift", 
    "delta": "0:00:01.158844", 
    "end": "2021-03-08 01:16:33.102108", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create -f https://raw.githubusercontent.com/DuncanDoyle/reactjs-openshift/master/create-react-app-openshift-template.yaml -n openshift", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:31.943264", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "template.template.openshift.io \"react-web-app\" created", 
    "stdout_lines": [
        "template.template.openshift.io \"react-web-app\" created"
    ]
}

# Module4 用のPostgreSQL DBのインストール
TASK [include_role] ************************************************************
task path: /opt/apb/actions/provision.yml:220

# roles/rhpam_reporting_database/tasks/main.yml
## rhpam_reporting_database : Check if the PostgreSQL database exists
TASK [rhpam_reporting_database : Check if the PostgreSQL database exists] ******
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166193.33-719183842735 `" && echo ansible-tmp-1615166193.33-719183842735="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166193.33-719183842735 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp5eeVPO TO /opt/apb/.ansible/tmp/ansible-tmp-1615166193.33-719183842735/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166193.33-719183842735/ /opt/apb/.ansible/tmp/ansible-tmp-1615166193.33-719183842735/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166193.33-719183842735/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166193.33-719183842735/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get dc/postgresql -n labs-infra", 
    "delta": "0:00:00.744355", 
    "end": "2021-03-08 01:16:34.350784", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get dc/postgresql -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:16:33.606429", 
    "stderr": "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"postgresql\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"postgresql\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## rhpam_reporting_database : Create PostgreSQL database
TASK [rhpam_reporting_database : Create PostgreSQL database] *******************
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166194.44-22178543983789 `" && echo ansible-tmp-1615166194.44-22178543983789="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166194.44-22178543983789 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpiemRAS TO /opt/apb/.ansible/tmp/ansible-tmp-1615166194.44-22178543983789/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166194.44-22178543983789/ /opt/apb/.ansible/tmp/ansible-tmp-1615166194.44-22178543983789/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166194.44-22178543983789/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166194.44-22178543983789/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --template=postgresql-ephemeral -p NAMESPACE=openshift -p POSTGRESQL_DATABASE=postgres -p POSTGRESQL_USER=postgres -p POSTGRESQL_PASSWORD=postgres -n labs-infra", 
    "delta": "0:00:01.107653", 
    "end": "2021-03-08 01:16:35.831392", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --template=postgresql-ephemeral -p NAMESPACE=openshift -p POSTGRESQL_DATABASE=postgres -p POSTGRESQL_USER=postgres -p POSTGRESQL_PASSWORD=postgres -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:34.723739", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Deploying template \"openshift/postgresql-ephemeral\" to project labs-infra\n\n     PostgreSQL (Ephemeral)\n     ---------\n     PostgreSQL database service, without persistent storage. For more information about using this template, including OpenShift considerations, see https://github.com/sclorg/postgresql-container/.\n     \n     WARNING: Any data stored will be lost upon pod destruction. Only use this template for testing\n\n     The following service(s) have been created in your project: postgresql.\n     \n            Username: postgres\n            Password: postgres\n       Database Name: postgres\n      Connection URL: postgresql://postgresql:5432/\n     \n     For more information about using this template, including OpenShift considerations, see https://github.com/sclorg/postgresql-container/.\n\n     * With parameters:\n        * Memory Limit=512Mi\n        * Namespace=openshift\n        * Database Service Name=postgresql\n        * PostgreSQL Connection Username=postgres\n        * PostgreSQL Connection Password=postgres\n        * PostgreSQL Database Name=postgres\n        * Version of PostgreSQL Image=10-el8\n\n--> Creating resources ...\n    secret \"postgresql\" created\n    service \"postgresql\" created\n    deploymentconfig \"postgresql\" created\n--> Success\n    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:\n     'oc expose svc/postgresql' \n    Run 'oc status' to view your app.", 
    "stdout_lines": [
        "--> Deploying template \"openshift/postgresql-ephemeral\" to project labs-infra", 
        "", 
        "     PostgreSQL (Ephemeral)", 
        "     ---------", 
        "     PostgreSQL database service, without persistent storage. For more information about using this template, including OpenShift considerations, see https://github.com/sclorg/postgresql-container/.", 
        "     ", 
        "     WARNING: Any data stored will be lost upon pod destruction. Only use this template for testing", 
        "", 
        "     The following service(s) have been created in your project: postgresql.", 
        "     ", 
        "            Username: postgres", 
        "            Password: postgres", 
        "       Database Name: postgres", 
        "      Connection URL: postgresql://postgresql:5432/", 
        "     ", 
        "     For more information about using this template, including OpenShift considerations, see https://github.com/sclorg/postgresql-container/.", 
        "", 
        "     * With parameters:", 
        "        * Memory Limit=512Mi", 
        "        * Namespace=openshift", 
        "        * Database Service Name=postgresql", 
        "        * PostgreSQL Connection Username=postgres", 
        "        * PostgreSQL Connection Password=postgres", 
        "        * PostgreSQL Database Name=postgres", 
        "        * Version of PostgreSQL Image=10-el8", 
        "", 
        "--> Creating resources ...", 
        "    secret \"postgresql\" created", 
        "    service \"postgresql\" created", 
        "    deploymentconfig \"postgresql\" created", 
        "--> Success", 
        "    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:", 
        "     'oc expose svc/postgresql' ", 
        "    Run 'oc status' to view your app."
    ]
}

## rhpam_reporting_database : Check if ConfigMap exists
TASK [rhpam_reporting_database : Check if ConfigMap exists] ********************
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166195.93-84783796330533 `" && echo ansible-tmp-1615166195.93-84783796330533="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166195.93-84783796330533 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpTj45Fq TO /opt/apb/.ansible/tmp/ansible-tmp-1615166195.93-84783796330533/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166195.93-84783796330533/ /opt/apb/.ansible/tmp/ansible-tmp-1615166195.93-84783796330533/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166195.93-84783796330533/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166195.93-84783796330533/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get cm/postgresql-config-map -n labs-infra", 
    "delta": "0:00:00.788010", 
    "end": "2021-03-08 01:16:37.003264", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get cm/postgresql-config-map -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:16:36.215254", 
    "stderr": "Error from server (NotFound): configmaps \"postgresql-config-map\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): configmaps \"postgresql-config-map\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## rhpam_reporting_database : Create ConfigMap
TASK [rhpam_reporting_database : Create ConfigMap] *****************************
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:19
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166197.11-161759088536671 `" && echo ansible-tmp-1615166197.11-161759088536671="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166197.11-161759088536671 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpt9bo_g TO /opt/apb/.ansible/tmp/ansible-tmp-1615166197.11-161759088536671/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166197.11-161759088536671/ /opt/apb/.ansible/tmp/ansible-tmp-1615166197.11-161759088536671/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166197.11-161759088536671/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166197.11-161759088536671/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create configmap postgresql-config-map --from-file=/opt/ansible/roles/rhpam_reporting_database/files/provision_data.sh --from-file=/opt/ansible/roles/rhpam_reporting_database/files/wait_for_postgres.sh --from-file=/opt/ansible/roles/rhpam_reporting_database/files/provision_test_data.sql -n labs-infra", 
    "delta": "0:00:00.793199", 
    "end": "2021-03-08 01:16:38.139931", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create configmap postgresql-config-map --from-file=/opt/ansible/roles/rhpam_reporting_database/files/provision_data.sh --from-file=/opt/ansible/roles/rhpam_reporting_database/files/wait_for_postgres.sh --from-file=/opt/ansible/roles/rhpam_reporting_database/files/provision_test_data.sql -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:37.346732", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "configmap \"postgresql-config-map\" created", 
    "stdout_lines": [
        "configmap \"postgresql-config-map\" created"
    ]
}

## rhpam_reporting_database : Set label on ConfigMap
TASK [rhpam_reporting_database : Set label on ConfigMap] ***********************
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:23
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166198.24-14568098991644 `" && echo ansible-tmp-1615166198.24-14568098991644="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166198.24-14568098991644 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpPQK2yr TO /opt/apb/.ansible/tmp/ansible-tmp-1615166198.24-14568098991644/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166198.24-14568098991644/ /opt/apb/.ansible/tmp/ansible-tmp-1615166198.24-14568098991644/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166198.24-14568098991644/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166198.24-14568098991644/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc label cm postgresql-config-map app=postgresql-ephemeral -n labs-infra", 
    "delta": "0:00:00.791346", 
    "end": "2021-03-08 01:16:39.325011", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc label cm postgresql-config-map app=postgresql-ephemeral -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:38.533665", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "configmap \"postgresql-config-map\" labeled", 
    "stdout_lines": [
        "configmap \"postgresql-config-map\" labeled"
    ]
}

## rhpam_reporting_database : Attach ConfigMap
TASK [rhpam_reporting_database : Attach ConfigMap] *****************************
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:27
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166199.41-251648775945538 `" && echo ansible-tmp-1615166199.41-251648775945538="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166199.41-251648775945538 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpT1N5bF TO /opt/apb/.ansible/tmp/ansible-tmp-1615166199.41-251648775945538/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166199.41-251648775945538/ /opt/apb/.ansible/tmp/ansible-tmp-1615166199.41-251648775945538/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166199.41-251648775945538/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166199.41-251648775945538/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set volume dc/postgresql --name=postgresql-config-volume --add -m /tmp/config-files -t configmap --configmap-name=postgresql-config-map -n labs-infra", 
    "delta": "0:00:00.857243", 
    "end": "2021-03-08 01:16:40.505093", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set volume dc/postgresql --name=postgresql-config-volume --add -m /tmp/config-files -t configmap --configmap-name=postgresql-config-map -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:39.647850", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"postgresql\" updated", 
    "stdout_lines": [
        "deploymentconfig \"postgresql\" updated"
    ]
}

## rhpam_reporting_database : Set ConfigMap
TASK [rhpam_reporting_database : Set ConfigMap] ********************************
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:32
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166200.63-185259455375170 `" && echo ansible-tmp-1615166200.63-185259455375170="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166200.63-185259455375170 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpOhikI0 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166200.63-185259455375170/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166200.63-185259455375170/ /opt/apb/.ansible/tmp/ansible-tmp-1615166200.63-185259455375170/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166200.63-185259455375170/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166200.63-185259455375170/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env --from=configmap/postgresql-config-map dc/postgresql -n labs-infra", 
    "delta": "0:00:00.931751", 
    "end": "2021-03-08 01:16:41.850590", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env --from=configmap/postgresql-config-map dc/postgresql -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:40.918839", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"postgresql\" updated", 
    "stdout_lines": [
        "deploymentconfig \"postgresql\" updated"
    ]
}

## rhpam_reporting_database : Set Deployment Hooks
TASK [rhpam_reporting_database : Set Deployment Hooks] *************************
task path: /opt/ansible/roles/rhpam_reporting_database/tasks/main.yml:36
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166201.93-71907562755974 `" && echo ansible-tmp-1615166201.93-71907562755974="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166201.93-71907562755974 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmphMYiYx TO /opt/apb/.ansible/tmp/ansible-tmp-1615166201.93-71907562755974/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166201.93-71907562755974/ /opt/apb/.ansible/tmp/ansible-tmp-1615166201.93-71907562755974/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166201.93-71907562755974/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166201.93-71907562755974/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set deployment-hook dc/postgresql --post -c postgresql -e POSTGRESQL_HOSTNAME=postgresql -e POSTGRESQL_USER=postgres -e POSTGRESQL_PASSWORD=postgres --volumes=postgresql-config-volume --failure-policy=abort -- /bin/bash /tmp/config-files/wait_for_postgres.sh /tmp/config-files/provision_data.sh -n labs-infra", 
    "delta": "0:00:00.839470", 
    "end": "2021-03-08 01:16:43.059272", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set deployment-hook dc/postgresql --post -c postgresql -e POSTGRESQL_HOSTNAME=postgresql -e POSTGRESQL_USER=postgres -e POSTGRESQL_PASSWORD=postgres --volumes=postgresql-config-volume --failure-policy=abort -- /bin/bash /tmp/config-files/wait_for_postgres.sh /tmp/config-files/provision_data.sh -n labs-infra", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:42.219802", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"postgresql\" updated", 
    "stdout_lines": [
        "deploymentconfig \"postgresql\" updated"
    ]
}

# 各ユーザーのプロジェクト作成
TASK [include_role] ************************************************************
task path: /opt/apb/actions/provision.yml:226

## rhpam_project : Check if project exists
TASK [rhpam_project : Check if project exists] *********************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166203.53-122502558681210 `" && echo ansible-tmp-1615166203.53-122502558681210="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166203.53-122502558681210 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpB_Nu8m TO /opt/apb/.ansible/tmp/ansible-tmp-1615166203.53-122502558681210/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166203.53-122502558681210/ /opt/apb/.ansible/tmp/ansible-tmp-1615166203.53-122502558681210/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166203.53-122502558681210/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166203.53-122502558681210/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get project rhpam-user1", 
    "delta": "0:00:00.886411", 
    "end": "2021-03-08 01:16:44.704335", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:16:43.817924", 
    "stderr": "Error from server (NotFound): namespaces \"rhpam-user1\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): namespaces \"rhpam-user1\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## rhpam_project : Create projects
TASK [rhpam_project : Create projects] *****************************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166204.81-77815716355621 `" && echo ansible-tmp-1615166204.81-77815716355621="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166204.81-77815716355621 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp8E2TkL TO /opt/apb/.ansible/tmp/ansible-tmp-1615166204.81-77815716355621/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166204.81-77815716355621/ /opt/apb/.ansible/tmp/ansible-tmp-1615166204.81-77815716355621/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166204.81-77815716355621/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166204.81-77815716355621/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-project rhpam-user1 --display-name=\"RHPAM 7.9.0 - User 1\" --description=\"RHPAM 7.9 for user 1.\"", 
    "delta": "0:00:00.934163", 
    "end": "2021-03-08 01:16:46.043546", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-project rhpam-user1 --display-name=\"RHPAM 7.9.0 - User 1\" --description=\"RHPAM 7.9 for user 1.\"", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:45.109383", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "Now using project \"rhpam-user1\" on server \"https://kubernetes.default:443\".\n\nYou can add applications to this project with the 'new-app' command. For example, try:\n\n    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git\n\nto build a new example application in Ruby.", 
    "stdout_lines": [
        "Now using project \"rhpam-user1\" on server \"https://kubernetes.default:443\".", 
        "", 
        "You can add applications to this project with the 'new-app' command. For example, try:", 
        "", 
        "    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git", 
        "", 
        "to build a new example application in Ruby."
    ]
}

## rhpam_project : Annotate project namespace
TASK [rhpam_project : Annotate project namespace] ******************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166206.12-168024197721830 `" && echo ansible-tmp-1615166206.12-168024197721830="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166206.12-168024197721830 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpmXp_Ml TO /opt/apb/.ansible/tmp/ansible-tmp-1615166206.12-168024197721830/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166206.12-168024197721830/ /opt/apb/.ansible/tmp/ansible-tmp-1615166206.12-168024197721830/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166206.12-168024197721830/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166206.12-168024197721830/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc annotate namespace rhpam-user1 openshift.io/requester=user1 --overwrite", 
    "delta": "0:00:00.833087", 
    "end": "2021-03-08 01:16:47.261302", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc annotate namespace rhpam-user1 openshift.io/requester=user1 --overwrite", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:46.428215", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "namespace \"rhpam-user1\" annotated", 
    "stdout_lines": [
        "namespace \"rhpam-user1\" annotated"
    ]
}

## rhpam_project : Make user admin
TASK [rhpam_project : Make user admin] *****************************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166207.41-122639732082916 `" && echo ansible-tmp-1615166207.41-122639732082916="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166207.41-122639732082916 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp8ncWEP TO /opt/apb/.ansible/tmp/ansible-tmp-1615166207.41-122639732082916/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166207.41-122639732082916/ /opt/apb/.ansible/tmp/ansible-tmp-1615166207.41-122639732082916/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166207.41-122639732082916/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166207.41-122639732082916/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc policy add-role-to-user admin user1 -n rhpam-user1", 
    "delta": "0:00:00.765003", 
    "end": "2021-03-08 01:16:48.479026", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc policy add-role-to-user admin user1 -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:47.714023", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "role \"admin\" added: \"user1\"", 
    "stdout_lines": [
        "role \"admin\" added: \"user1\""
    ]
}

# 繰り返し(User2)
TASK [rhpam_project : Check if project exists] *********************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166208.6-139372805131610 `" && echo ansible-tmp-1615166208.6-139372805131610="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166208.6-139372805131610 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpijB1IN TO /opt/apb/.ansible/tmp/ansible-tmp-1615166208.6-139372805131610/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166208.6-139372805131610/ /opt/apb/.ansible/tmp/ansible-tmp-1615166208.6-139372805131610/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166208.6-139372805131610/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166208.6-139372805131610/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get project rhpam-user2", 
    "delta": "0:00:00.926371", 
    "end": "2021-03-08 01:16:49.767766", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:16:48.841395", 
    "stderr": "Error from server (NotFound): namespaces \"rhpam-user2\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): namespaces \"rhpam-user2\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [rhpam_project : Create projects] *****************************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166209.91-98320589500524 `" && echo ansible-tmp-1615166209.91-98320589500524="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166209.91-98320589500524 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpW64zKz TO /opt/apb/.ansible/tmp/ansible-tmp-1615166209.91-98320589500524/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166209.91-98320589500524/ /opt/apb/.ansible/tmp/ansible-tmp-1615166209.91-98320589500524/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166209.91-98320589500524/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166209.91-98320589500524/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-project rhpam-user2 --display-name=\"RHPAM 7.9.0 - User 2\" --description=\"RHPAM 7.9 for user 2.\"", 
    "delta": "0:00:01.067773", 
    "end": "2021-03-08 01:16:51.211180", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-project rhpam-user2 --display-name=\"RHPAM 7.9.0 - User 2\" --description=\"RHPAM 7.9 for user 2.\"", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:50.143407", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "Now using project \"rhpam-user2\" on server \"https://kubernetes.default:443\".\n\nYou can add applications to this project with the 'new-app' command. For example, try:\n\n    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git\n\nto build a new example application in Ruby.", 
    "stdout_lines": [
        "Now using project \"rhpam-user2\" on server \"https://kubernetes.default:443\".", 
        "", 
        "You can add applications to this project with the 'new-app' command. For example, try:", 
        "", 
        "    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git", 
        "", 
        "to build a new example application in Ruby."
    ]
}

TASK [rhpam_project : Annotate project namespace] ******************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166211.32-13921228267992 `" && echo ansible-tmp-1615166211.32-13921228267992="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166211.32-13921228267992 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpEV7xyp TO /opt/apb/.ansible/tmp/ansible-tmp-1615166211.32-13921228267992/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166211.32-13921228267992/ /opt/apb/.ansible/tmp/ansible-tmp-1615166211.32-13921228267992/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166211.32-13921228267992/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166211.32-13921228267992/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc annotate namespace rhpam-user2 openshift.io/requester=user2 --overwrite", 
    "delta": "0:00:00.799600", 
    "end": "2021-03-08 01:16:52.401078", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc annotate namespace rhpam-user2 openshift.io/requester=user2 --overwrite", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:51.601478", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "namespace \"rhpam-user2\" annotated", 
    "stdout_lines": [
        "namespace \"rhpam-user2\" annotated"
    ]
}

TASK [rhpam_project : Make user admin] *****************************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166212.51-216387888960031 `" && echo ansible-tmp-1615166212.51-216387888960031="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166212.51-216387888960031 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp6hLFUi TO /opt/apb/.ansible/tmp/ansible-tmp-1615166212.51-216387888960031/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166212.51-216387888960031/ /opt/apb/.ansible/tmp/ansible-tmp-1615166212.51-216387888960031/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166212.51-216387888960031/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166212.51-216387888960031/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc policy add-role-to-user admin user2 -n rhpam-user2", 
    "delta": "0:00:00.739536", 
    "end": "2021-03-08 01:16:53.478885", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc policy add-role-to-user admin user2 -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:52.739349", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "role \"admin\" added: \"user2\"", 
    "stdout_lines": [
        "role \"admin\" added: \"user2\""
    ]
}

# 繰り返し(User3)
TASK [rhpam_project : Check if project exists] *********************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166213.54-20213711935123 `" && echo ansible-tmp-1615166213.54-20213711935123="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166213.54-20213711935123 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpwAoWjD TO /opt/apb/.ansible/tmp/ansible-tmp-1615166213.54-20213711935123/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166213.54-20213711935123/ /opt/apb/.ansible/tmp/ansible-tmp-1615166213.54-20213711935123/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166213.54-20213711935123/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166213.54-20213711935123/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get project rhpam-user3", 
    "delta": "0:00:00.988785", 
    "end": "2021-03-08 01:16:54.823559", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:16:53.834774", 
    "stderr": "Error from server (NotFound): namespaces \"rhpam-user3\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): namespaces \"rhpam-user3\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [rhpam_project : Create projects] *****************************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166214.93-200914547555947 `" && echo ansible-tmp-1615166214.93-200914547555947="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166214.93-200914547555947 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp5ZGsAv TO /opt/apb/.ansible/tmp/ansible-tmp-1615166214.93-200914547555947/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166214.93-200914547555947/ /opt/apb/.ansible/tmp/ansible-tmp-1615166214.93-200914547555947/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166214.93-200914547555947/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166214.93-200914547555947/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-project rhpam-user3 --display-name=\"RHPAM 7.9.0 - User 3\" --description=\"RHPAM 7.9 for user 3.\"", 
    "delta": "0:00:00.982384", 
    "end": "2021-03-08 01:16:56.190998", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-project rhpam-user3 --display-name=\"RHPAM 7.9.0 - User 3\" --description=\"RHPAM 7.9 for user 3.\"", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:55.208614", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "Now using project \"rhpam-user3\" on server \"https://kubernetes.default:443\".\n\nYou can add applications to this project with the 'new-app' command. For example, try:\n\n    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git\n\nto build a new example application in Ruby.", 
    "stdout_lines": [
        "Now using project \"rhpam-user3\" on server \"https://kubernetes.default:443\".", 
        "", 
        "You can add applications to this project with the 'new-app' command. For example, try:", 
        "", 
        "    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git", 
        "", 
        "to build a new example application in Ruby."
    ]
}

TASK [rhpam_project : Annotate project namespace] ******************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166216.3-144708581737615 `" && echo ansible-tmp-1615166216.3-144708581737615="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166216.3-144708581737615 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmprfWrIW TO /opt/apb/.ansible/tmp/ansible-tmp-1615166216.3-144708581737615/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166216.3-144708581737615/ /opt/apb/.ansible/tmp/ansible-tmp-1615166216.3-144708581737615/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166216.3-144708581737615/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166216.3-144708581737615/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc annotate namespace rhpam-user3 openshift.io/requester=user3 --overwrite", 
    "delta": "0:00:00.813651", 
    "end": "2021-03-08 01:16:57.351510", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc annotate namespace rhpam-user3 openshift.io/requester=user3 --overwrite", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:56.537859", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "namespace \"rhpam-user3\" annotated", 
    "stdout_lines": [
        "namespace \"rhpam-user3\" annotated"
    ]
}

TASK [rhpam_project : Make user admin] *****************************************
task path: /opt/ansible/roles/rhpam_project/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166217.44-105290285271454 `" && echo ansible-tmp-1615166217.44-105290285271454="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166217.44-105290285271454 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpRQ99LA TO /opt/apb/.ansible/tmp/ansible-tmp-1615166217.44-105290285271454/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166217.44-105290285271454/ /opt/apb/.ansible/tmp/ansible-tmp-1615166217.44-105290285271454/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166217.44-105290285271454/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166217.44-105290285271454/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc policy add-role-to-user admin user3 -n rhpam-user3", 
    "delta": "0:00:00.733030", 
    "end": "2021-03-08 01:16:58.453264", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc policy add-role-to-user admin user3 -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:57.720234", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "role \"admin\" added: \"user3\"", 
    "stdout_lines": [
        "role \"admin\" added: \"user3\""
    ]
}


# PAMのインストール - ansible_openshift_rhpam ??
TASK [include_role] ************************************************************
task path: /opt/apb/actions/provision.yml:239

## ansible_openshift_rhpam : debug
TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:3
ok: [localhost] => {
    "msg": [
        "Openshift project", 
        "-> Check if rhpam-user1 project exists"
    ]
}

## ansible_openshift_rhpam : check if rhpam-user1 project exists
TASK [ansible_openshift_rhpam : check if rhpam-user1 project exists] ***********
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:8
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166219.02-239022718008362 `" && echo ansible-tmp-1615166219.02-239022718008362="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166219.02-239022718008362 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp83sMSa TO /opt/apb/.ansible/tmp/ansible-tmp-1615166219.02-239022718008362/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166219.02-239022718008362/ /opt/apb/.ansible/tmp/ansible-tmp-1615166219.02-239022718008362/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166219.02-239022718008362/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166219.02-239022718008362/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "cmd": "oc get project rhpam-user1", 
    "delta": "0:00:00.747156", 
    "end": "2021-03-08 01:17:00.053042", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:16:59.305886", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME          DISPLAY NAME           STATUS\nrhpam-user1   RHPAM 7.9.0 - User 1   Active", 
    "stdout_lines": [
        "NAME          DISPLAY NAME           STATUS", 
        "rhpam-user1   RHPAM 7.9.0 - User 1   Active"
    ]
}

## ansible_openshift_rhpam : debug
TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:14
ok: [localhost] => {
    "msg": [
        "Openshift project", 
        "-> Create Openshift project (rhpam-user1)"
    ]
}

## ansible_openshift_rhpam : create rhpam-user1 project (必要だが、今回は前ステップで実施済み)
TASK [ansible_openshift_rhpam : create rhpam-user1 project] ********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:19
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

## ansible_openshift_rhpam : debug
TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:26
ok: [localhost] => {
    "msg": "-> Process RHPAM Template"
}

## ansible_openshift_rhpam : Check Secrets Business Central
TASK [ansible_openshift_rhpam : Check Secrets Business Central] ****************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:29
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166220.32-213607913214409 `" && echo ansible-tmp-1615166220.32-213607913214409="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166220.32-213607913214409 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpMMzZwB TO /opt/apb/.ansible/tmp/ansible-tmp-1615166220.32-213607913214409/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166220.32-213607913214409/ /opt/apb/.ansible/tmp/ansible-tmp-1615166220.32-213607913214409/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166220.32-213607913214409/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166220.32-213607913214409/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/businesscentral-app-secret -n rhpam-user1", 
    "delta": "0:00:00.778242", 
    "end": "2021-03-08 01:17:01.324113", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/businesscentral-app-secret -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:00.545871", 
    "stderr": "Error from server (NotFound): secrets \"businesscentral-app-secret\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"businesscentral-app-secret\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## ansible_openshift_rhpam : Create Secrets Business Central (必要)
TASK [ansible_openshift_rhpam : Create Secrets Business Central] ***************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:35
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166221.42-180039780399365 `" && echo ansible-tmp-1615166221.42-180039780399365="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166221.42-180039780399365 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpEnmRTG TO /opt/apb/.ansible/tmp/ansible-tmp-1615166221.42-180039780399365/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166221.42-180039780399365/ /opt/apb/.ansible/tmp/ansible-tmp-1615166221.42-180039780399365/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166221.42-180039780399365/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166221.42-180039780399365/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=businesscentral-app-secret | oc create -f - -n rhpam-user1", 
    "delta": "0:00:01.723798", 
    "end": "2021-03-08 01:17:03.367884", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=businesscentral-app-secret | oc create -f - -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:01.644086", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"businesscentral-app-secret\" created", 
    "stdout_lines": [
        "secret \"businesscentral-app-secret\" created"
    ]
}

## ansible_openshift_rhpam : Check Secrets KIE-Server
TASK [ansible_openshift_rhpam : Check Secrets KIE-Server] **********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:39
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166223.43-143280248363398 `" && echo ansible-tmp-1615166223.43-143280248363398="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166223.43-143280248363398 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpUP_CqN TO /opt/apb/.ansible/tmp/ansible-tmp-1615166223.43-143280248363398/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166223.43-143280248363398/ /opt/apb/.ansible/tmp/ansible-tmp-1615166223.43-143280248363398/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166223.43-143280248363398/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166223.43-143280248363398/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/kieserver-app-secret -n rhpam-user1", 
    "delta": "0:00:00.735784", 
    "end": "2021-03-08 01:17:04.448256", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/kieserver-app-secret -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:03.712472", 
    "stderr": "Error from server (NotFound): secrets \"kieserver-app-secret\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"kieserver-app-secret\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## ansible_openshift_rhpam : Create Secrets KIE-server (必要)
TASK [ansible_openshift_rhpam : Create Secrets KIE-server] *********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:45
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166224.54-30124783347326 `" && echo ansible-tmp-1615166224.54-30124783347326="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166224.54-30124783347326 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpt3fXcL TO /opt/apb/.ansible/tmp/ansible-tmp-1615166224.54-30124783347326/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166224.54-30124783347326/ /opt/apb/.ansible/tmp/ansible-tmp-1615166224.54-30124783347326/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166224.54-30124783347326/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166224.54-30124783347326/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=kieserver-app-secret | oc create -f - -n rhpam-user1", 
    "delta": "0:00:01.402952", 
    "end": "2021-03-08 01:17:06.234846", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=kieserver-app-secret | oc create -f - -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:04.831894", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"kieserver-app-secret\" created", 
    "stdout_lines": [
        "secret \"kieserver-app-secret\" created"
    ]
}

## ansible_openshift_rhpam : Check Generic Secret with RHPAM Credentials
TASK [ansible_openshift_rhpam : Check Generic Secret with RHPAM Credentials] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:49
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166226.31-254390135099471 `" && echo ansible-tmp-1615166226.31-254390135099471="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166226.31-254390135099471 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpwr7m_I TO /opt/apb/.ansible/tmp/ansible-tmp-1615166226.31-254390135099471/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166226.31-254390135099471/ /opt/apb/.ansible/tmp/ansible-tmp-1615166226.31-254390135099471/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166226.31-254390135099471/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166226.31-254390135099471/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/rhpam-credentials -n rhpam-user1", 
    "delta": "0:00:00.792482", 
    "end": "2021-03-08 01:17:07.329125", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/rhpam-credentials -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:06.536643", 
    "stderr": "Error from server (NotFound): secrets \"rhpam-credentials\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"rhpam-credentials\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## ansible_openshift_rhpam : Create Generic Secret with RHPAM Credentials (必要)
TASK [ansible_openshift_rhpam : Create Generic Secret with RHPAM Credentials] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:55
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166227.42-15098597683238 `" && echo ansible-tmp-1615166227.42-15098597683238="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166227.42-15098597683238 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp7hHVUi TO /opt/apb/.ansible/tmp/ansible-tmp-1615166227.42-15098597683238/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166227.42-15098597683238/ /opt/apb/.ansible/tmp/ansible-tmp-1615166227.42-15098597683238/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166227.42-15098597683238/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166227.42-15098597683238/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create secret generic rhpam-credentials --from-literal=KIE_ADMIN_USER=pamAdmin --from-literal=KIE_ADMIN_PWD=redhatpam1! -n rhpam-user1", 
    "delta": "0:00:00.802537", 
    "end": "2021-03-08 01:17:08.451472", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create secret generic rhpam-credentials --from-literal=KIE_ADMIN_USER=pamAdmin --from-literal=KIE_ADMIN_PWD=redhatpam1! -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:07.648935", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"rhpam-credentials\" created", 
    "stdout_lines": [
        "secret \"rhpam-credentials\" created"
    ]
}

## ansible_openshift_rhpam : check if RHPAM exists
TASK [ansible_openshift_rhpam : check if RHPAM exists] *************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:85
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166228.53-76871492824598 `" && echo ansible-tmp-1615166228.53-76871492824598="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166228.53-76871492824598 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpCXiQF1 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166228.53-76871492824598/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166228.53-76871492824598/ /opt/apb/.ansible/tmp/ansible-tmp-1615166228.53-76871492824598/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166228.53-76871492824598/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166228.53-76871492824598/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get dc/rhpam7-rhpamcentr -n rhpam-user1", 
    "delta": "0:00:00.746785", 
    "end": "2021-03-08 01:17:09.556499", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get dc/rhpam7-rhpamcentr -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:08.809714", 
    "stderr": "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"rhpam7-rhpamcentr\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"rhpam7-rhpamcentr\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## ansible_openshift_rhpam : Set base param fact (事前準備)
TASK [ansible_openshift_rhpam : Set base param fact] ***************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:91
ok: [localhost] => {
    "ansible_facts": {
        "TEMPLATE_PARAMS": "-p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\""
    }, 
    "changed": false
}

## ansible_openshift_rhpam : Set additional facts for non-trial environment (事前準備)
TASK [ansible_openshift_rhpam : Set additional facts for non-trial environment] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:95
ok: [localhost] => {
    "ansible_facts": {
        "TEMPLATE_PARAMS": "-p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials'"
    }, 
    "changed": false
}

## ansible_openshift_rhpam : Create PAM7 environment (必要)
TASK [ansible_openshift_rhpam : Create PAM7 environment] ***********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:100
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166229.82-226510233612179 `" && echo ansible-tmp-1615166229.82-226510233612179="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166229.82-226510233612179 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp_c_Ksh TO /opt/apb/.ansible/tmp/ansible-tmp-1615166229.82-226510233612179/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166229.82-226510233612179/ /opt/apb/.ansible/tmp/ansible-tmp-1615166229.82-226510233612179/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166229.82-226510233612179/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166229.82-226510233612179/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --template=rhpam79-authoring -p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials' -p IMAGE_STREAM_NAMESPACE=openshift -n rhpam-user1", 
    "delta": "0:00:01.359791", 
    "end": "2021-03-08 01:17:11.403936", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --template=rhpam79-authoring -p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials' -p IMAGE_STREAM_NAMESPACE=openshift -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:10.044145", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Deploying template \"openshift/rhpam79-authoring\" to project rhpam-user1\n\n     Red Hat Process Automation Manager 7.9 authoring environment (non-HA, persistent, with https)\n     ---------\n     Application template for a non-HA persistent authoring environment, for Red Hat Process Automation Manager 7.9 - Deprecated\n\n     A new persistent Process Automation Manager application have been created in your project.\n     The username/password needed for accessing the application are stored in \"rhpam-credentials\" secret as\n     KIE_ADMIN_USER and KIE_ADMIN_PWD\n     \n     You must create the secret named \"rhpam-credentials\" containing the KIE_ADMIN_USER and KIE_ADMIN_PWD values and the secrets named \"businesscentral-app-secret\" and \"kieserver-app-secret\"\n     containing the keystore.jks and keystore.jks files used for serving secure content.\n\n     * With parameters:\n        * Application Name=rhpam7\n        * Credentials secret=rhpam-credentials\n        * KIE Server Controller Token=\n        * KIE Server Bypass Auth User=false\n        * KIE Server Persistence DS=java:/jboss/datasources/rhpam\n        * KIE Server H2 Database User=sa\n        * KIE Server H2 Database Password=yLKEWe0! # generated\n        * KIE Server Mode=DEVELOPMENT\n        * KIE MBeans=enabled\n        * Drools Server Filter Classes=true\n        * Prometheus Server Extension Disabled=\n        * Business Central Custom http Route Hostname=\n        * Business Central Custom https Route Hostname=\n        * KIE Server Custom http Route Hostname=\n        * KIE Server Custom https Route Hostname=\n        * Business Central Server Keystore Secret Name=businesscentral-app-secret\n        * Business Central Server Keystore Filename=keystore.jks\n        * Business Central Server Certificate Name=jboss\n        * Business Central Server Keystore Password=mykeystorepass\n        * KIE Server Keystore Secret Name=kieserver-app-secret\n        * KIE Server Keystore Filename=keystore.jks\n        * KIE Server Certificate Name=jboss\n        * KIE Server Keystore Password=mykeystorepass\n        * Database Volume Capacity=1Gi\n        * Enable KIE server global discovery=false\n        * Prefer KIE Server OpenShift Service=true\n        * KIE ServerTemplate Cache TTL=5000\n        * ImageStream Namespace=openshift\n        * KIE Server ImageStream Name=rhpam-kieserver-rhel8\n        * ImageStream Tag=7.9.0\n        * Maven mirror URL=\n        * Maven mirror of=external:*,!repo-rhpamcentr\n        * Maven repository ID=repo-custom\n        * Maven repository URL=\n        * Maven repository user name=\n        * Maven repository password=\n        * Git hooks directory=\n        * Business Central Volume Capacity=1Gi\n        * Business Central Container Memory Limit=6Gi\n        * KIE Server Container Memory Limit=1Gi\n        * RH-SSO URL=\n        * RH-SSO Realm name=\n        * Business Central RH-SSO Client name=\n        * Business Central RH-SSO Client Secret=\n        * KIE Server RH-SSO Client name=\n        * KIE Server RH-SSO Client Secret=\n        * RH-SSO Realm admin user name=\n        * RH-SSO Realm Admin Password=\n        * RH-SSO Disable SSL Certificate Validation=false\n        * RH-SSO Principal Attribute=preferred_username\n        * LDAP Endpoint=\n        * LDAP Bind DN=\n        * LDAP Bind Credentials=\n        * LDAP JAAS Security Domain=\n        * LDAP Base DN=\n        * LDAP Base Search filter=\n        * LDAP Search scope=\n        * LDAP Search time limit=\n        * LDAP DN attribute=\n        * LDAP Parse username=\n        * LDAP Username begin string=\n        * LDAP Username end string=\n        * LDAP Role attributeID=\n        * LDAP Roles Search DN=\n        * LDAP Role search filter=\n        * LDAP Role recursion=\n        * LDAP Default role=\n        * LDAP Role name attribute ID=\n        * LDAP Role DN contains roleNameAttributeID=\n        * LDAP Role Attribute ID is DN=\n        * LDAP Referral user attribute ID=\n        * RoleMapping rolesProperties file path=\n        * RoleMapping replaceRole property=\n\n--> Creating resources ...\n    serviceaccount \"rhpam7-rhpamsvc\" created\n    rolebinding \"rhpam7-rhpamsvc-edit\" created\n    service \"rhpam7-rhpamcentr\" created\n    service \"rhpam7-kieserver\" created\n    route \"insecure-rhpam7-rhpamcentr\" created\n    route \"rhpam7-rhpamcentr\" created\n    route \"insecure-rhpam7-kieserver\" created\n    route \"rhpam7-kieserver\" created\n    deploymentconfig \"rhpam7-rhpamcentr\" created\n    deploymentconfig \"rhpam7-kieserver\" created\n    persistentvolumeclaim \"rhpam7-rhpamcentr-claim\" created\n    persistentvolumeclaim \"rhpam7-kie-claim\" created\n--> Success\n    Access your application via route 'insecure-rhpam7-rhpamcentr-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'rhpam7-rhpamcentr-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'insecure-rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Run 'oc status' to view your app.", 
    "stdout_lines": [
        "--> Deploying template \"openshift/rhpam79-authoring\" to project rhpam-user1", 
        "", 
        "     Red Hat Process Automation Manager 7.9 authoring environment (non-HA, persistent, with https)", 
        "     ---------", 
        "     Application template for a non-HA persistent authoring environment, for Red Hat Process Automation Manager 7.9 - Deprecated", 
        "", 
        "     A new persistent Process Automation Manager application have been created in your project.", 
        "     The username/password needed for accessing the application are stored in \"rhpam-credentials\" secret as", 
        "     KIE_ADMIN_USER and KIE_ADMIN_PWD", 
        "     ", 
        "     You must create the secret named \"rhpam-credentials\" containing the KIE_ADMIN_USER and KIE_ADMIN_PWD values and the secrets named \"businesscentral-app-secret\" and \"kieserver-app-secret\"", 
        "     containing the keystore.jks and keystore.jks files used for serving secure content.", 
        "", 
        "     * With parameters:", 
        "        * Application Name=rhpam7", 
        "        * Credentials secret=rhpam-credentials", 
        "        * KIE Server Controller Token=", 
        "        * KIE Server Bypass Auth User=false", 
        "        * KIE Server Persistence DS=java:/jboss/datasources/rhpam", 
        "        * KIE Server H2 Database User=sa", 
        "        * KIE Server H2 Database Password=yLKEWe0! # generated", 
        "        * KIE Server Mode=DEVELOPMENT", 
        "        * KIE MBeans=enabled", 
        "        * Drools Server Filter Classes=true", 
        "        * Prometheus Server Extension Disabled=", 
        "        * Business Central Custom http Route Hostname=", 
        "        * Business Central Custom https Route Hostname=", 
        "        * KIE Server Custom http Route Hostname=", 
        "        * KIE Server Custom https Route Hostname=", 
        "        * Business Central Server Keystore Secret Name=businesscentral-app-secret", 
        "        * Business Central Server Keystore Filename=keystore.jks", 
        "        * Business Central Server Certificate Name=jboss", 
        "        * Business Central Server Keystore Password=mykeystorepass", 
        "        * KIE Server Keystore Secret Name=kieserver-app-secret", 
        "        * KIE Server Keystore Filename=keystore.jks", 
        "        * KIE Server Certificate Name=jboss", 
        "        * KIE Server Keystore Password=mykeystorepass", 
        "        * Database Volume Capacity=1Gi", 
        "        * Enable KIE server global discovery=false", 
        "        * Prefer KIE Server OpenShift Service=true", 
        "        * KIE ServerTemplate Cache TTL=5000", 
        "        * ImageStream Namespace=openshift", 
        "        * KIE Server ImageStream Name=rhpam-kieserver-rhel8", 
        "        * ImageStream Tag=7.9.0", 
        "        * Maven mirror URL=", 
        "        * Maven mirror of=external:*,!repo-rhpamcentr", 
        "        * Maven repository ID=repo-custom", 
        "        * Maven repository URL=", 
        "        * Maven repository user name=", 
        "        * Maven repository password=", 
        "        * Git hooks directory=", 
        "        * Business Central Volume Capacity=1Gi", 
        "        * Business Central Container Memory Limit=6Gi", 
        "        * KIE Server Container Memory Limit=1Gi", 
        "        * RH-SSO URL=", 
        "        * RH-SSO Realm name=", 
        "        * Business Central RH-SSO Client name=", 
        "        * Business Central RH-SSO Client Secret=", 
        "        * KIE Server RH-SSO Client name=", 
        "        * KIE Server RH-SSO Client Secret=", 
        "        * RH-SSO Realm admin user name=", 
        "        * RH-SSO Realm Admin Password=", 
        "        * RH-SSO Disable SSL Certificate Validation=false", 
        "        * RH-SSO Principal Attribute=preferred_username", 
        "        * LDAP Endpoint=", 
        "        * LDAP Bind DN=", 
        "        * LDAP Bind Credentials=", 
        "        * LDAP JAAS Security Domain=", 
        "        * LDAP Base DN=", 
        "        * LDAP Base Search filter=", 
        "        * LDAP Search scope=", 
        "        * LDAP Search time limit=", 
        "        * LDAP DN attribute=", 
        "        * LDAP Parse username=", 
        "        * LDAP Username begin string=", 
        "        * LDAP Username end string=", 
        "        * LDAP Role attributeID=", 
        "        * LDAP Roles Search DN=", 
        "        * LDAP Role search filter=", 
        "        * LDAP Role recursion=", 
        "        * LDAP Default role=", 
        "        * LDAP Role name attribute ID=", 
        "        * LDAP Role DN contains roleNameAttributeID=", 
        "        * LDAP Role Attribute ID is DN=", 
        "        * LDAP Referral user attribute ID=", 
        "        * RoleMapping rolesProperties file path=", 
        "        * RoleMapping replaceRole property=", 
        "", 
        "--> Creating resources ...", 
        "    serviceaccount \"rhpam7-rhpamsvc\" created", 
        "    rolebinding \"rhpam7-rhpamsvc-edit\" created", 
        "    service \"rhpam7-rhpamcentr\" created", 
        "    service \"rhpam7-kieserver\" created", 
        "    route \"insecure-rhpam7-rhpamcentr\" created", 
        "    route \"rhpam7-rhpamcentr\" created", 
        "    route \"insecure-rhpam7-kieserver\" created", 
        "    route \"rhpam7-kieserver\" created", 
        "    deploymentconfig \"rhpam7-rhpamcentr\" created", 
        "    deploymentconfig \"rhpam7-kieserver\" created", 
        "    persistentvolumeclaim \"rhpam7-rhpamcentr-claim\" created", 
        "    persistentvolumeclaim \"rhpam7-kie-claim\" created", 
        "--> Success", 
        "    Access your application via route 'insecure-rhpam7-rhpamcentr-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'rhpam7-rhpamcentr-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'insecure-rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Run 'oc status' to view your app."
    ]
}


## 繰り返し(USER2) 
TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:3
ok: [localhost] => {
    "msg": [
        "Openshift project", 
        "-> Check if rhpam-user2 project exists"
    ]
}

TASK [ansible_openshift_rhpam : check if rhpam-user2 project exists] ***********
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:8
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166231.53-67272010867415 `" && echo ansible-tmp-1615166231.53-67272010867415="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166231.53-67272010867415 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpy6BWfi TO /opt/apb/.ansible/tmp/ansible-tmp-1615166231.53-67272010867415/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166231.53-67272010867415/ /opt/apb/.ansible/tmp/ansible-tmp-1615166231.53-67272010867415/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166231.53-67272010867415/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166231.53-67272010867415/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "cmd": "oc get project rhpam-user2", 
    "delta": "0:00:00.785188", 
    "end": "2021-03-08 01:17:12.603317", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:11.818129", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME          DISPLAY NAME           STATUS\nrhpam-user2   RHPAM 7.9.0 - User 2   Active", 
    "stdout_lines": [
        "NAME          DISPLAY NAME           STATUS", 
        "rhpam-user2   RHPAM 7.9.0 - User 2   Active"
    ]
}

TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:14
ok: [localhost] => {
    "msg": [
        "Openshift project", 
        "-> Create Openshift project (rhpam-user2)"
    ]
}

TASK [ansible_openshift_rhpam : create rhpam-user2 project] ********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:19
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:26
ok: [localhost] => {
    "msg": "-> Process RHPAM Template"
}

TASK [ansible_openshift_rhpam : Check Secrets Business Central] ****************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:29
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166233.01-91072670038193 `" && echo ansible-tmp-1615166233.01-91072670038193="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166233.01-91072670038193 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpwUNXvw TO /opt/apb/.ansible/tmp/ansible-tmp-1615166233.01-91072670038193/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166233.01-91072670038193/ /opt/apb/.ansible/tmp/ansible-tmp-1615166233.01-91072670038193/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166233.01-91072670038193/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166233.01-91072670038193/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/businesscentral-app-secret -n rhpam-user2", 
    "delta": "0:00:00.877681", 
    "end": "2021-03-08 01:17:14.115507", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/businesscentral-app-secret -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:13.237826", 
    "stderr": "Error from server (NotFound): secrets \"businesscentral-app-secret\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"businesscentral-app-secret\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Create Secrets Business Central] ***************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:35
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166234.21-23888641186073 `" && echo ansible-tmp-1615166234.21-23888641186073="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166234.21-23888641186073 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpAKzOxR TO /opt/apb/.ansible/tmp/ansible-tmp-1615166234.21-23888641186073/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166234.21-23888641186073/ /opt/apb/.ansible/tmp/ansible-tmp-1615166234.21-23888641186073/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166234.21-23888641186073/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166234.21-23888641186073/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=businesscentral-app-secret | oc create -f - -n rhpam-user2", 
    "delta": "0:00:01.384470", 
    "end": "2021-03-08 01:17:15.826117", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=businesscentral-app-secret | oc create -f - -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:14.441647", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"businesscentral-app-secret\" created", 
    "stdout_lines": [
        "secret \"businesscentral-app-secret\" created"
    ]
}

TASK [ansible_openshift_rhpam : Check Secrets KIE-Server] **********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:39
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166235.92-235403217599215 `" && echo ansible-tmp-1615166235.92-235403217599215="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166235.92-235403217599215 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpkDdGeh TO /opt/apb/.ansible/tmp/ansible-tmp-1615166235.92-235403217599215/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166235.92-235403217599215/ /opt/apb/.ansible/tmp/ansible-tmp-1615166235.92-235403217599215/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166235.92-235403217599215/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166235.92-235403217599215/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/kieserver-app-secret -n rhpam-user2", 
    "delta": "0:00:00.790795", 
    "end": "2021-03-08 01:17:16.938342", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/kieserver-app-secret -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:16.147547", 
    "stderr": "Error from server (NotFound): secrets \"kieserver-app-secret\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"kieserver-app-secret\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Create Secrets KIE-server] *********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:45
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166237.02-37831870027015 `" && echo ansible-tmp-1615166237.02-37831870027015="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166237.02-37831870027015 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpzJAv4E TO /opt/apb/.ansible/tmp/ansible-tmp-1615166237.02-37831870027015/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166237.02-37831870027015/ /opt/apb/.ansible/tmp/ansible-tmp-1615166237.02-37831870027015/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166237.02-37831870027015/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166237.02-37831870027015/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=kieserver-app-secret | oc create -f - -n rhpam-user2", 
    "delta": "0:00:01.327756", 
    "end": "2021-03-08 01:17:18.630155", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=kieserver-app-secret | oc create -f - -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:17.302399", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"kieserver-app-secret\" created", 
    "stdout_lines": [
        "secret \"kieserver-app-secret\" created"
    ]
}

TASK [ansible_openshift_rhpam : Check Generic Secret with RHPAM Credentials] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:49
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166238.72-94292494099 `" && echo ansible-tmp-1615166238.72-94292494099="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166238.72-94292494099 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpCU2HfV TO /opt/apb/.ansible/tmp/ansible-tmp-1615166238.72-94292494099/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166238.72-94292494099/ /opt/apb/.ansible/tmp/ansible-tmp-1615166238.72-94292494099/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166238.72-94292494099/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166238.72-94292494099/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/rhpam-credentials -n rhpam-user2", 
    "delta": "0:00:00.791091", 
    "end": "2021-03-08 01:17:19.738135", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/rhpam-credentials -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:18.947044", 
    "stderr": "Error from server (NotFound): secrets \"rhpam-credentials\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"rhpam-credentials\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Create Generic Secret with RHPAM Credentials] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:55
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166239.83-230877192649796 `" && echo ansible-tmp-1615166239.83-230877192649796="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166239.83-230877192649796 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpdabxJ5 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166239.83-230877192649796/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166239.83-230877192649796/ /opt/apb/.ansible/tmp/ansible-tmp-1615166239.83-230877192649796/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166239.83-230877192649796/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166239.83-230877192649796/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create secret generic rhpam-credentials --from-literal=KIE_ADMIN_USER=pamAdmin --from-literal=KIE_ADMIN_PWD=redhatpam1! -n rhpam-user2", 
    "delta": "0:00:00.724232", 
    "end": "2021-03-08 01:17:20.833605", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create secret generic rhpam-credentials --from-literal=KIE_ADMIN_USER=pamAdmin --from-literal=KIE_ADMIN_PWD=redhatpam1! -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:20.109373", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"rhpam-credentials\" created", 
    "stdout_lines": [
        "secret \"rhpam-credentials\" created"
    ]
}

TASK [ansible_openshift_rhpam : check if RHPAM exists] *************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:85
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166240.93-90458183778202 `" && echo ansible-tmp-1615166240.93-90458183778202="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166240.93-90458183778202 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpb5qi5o TO /opt/apb/.ansible/tmp/ansible-tmp-1615166240.93-90458183778202/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166240.93-90458183778202/ /opt/apb/.ansible/tmp/ansible-tmp-1615166240.93-90458183778202/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166240.93-90458183778202/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166240.93-90458183778202/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get dc/rhpam7-rhpamcentr -n rhpam-user2", 
    "delta": "0:00:00.742084", 
    "end": "2021-03-08 01:17:21.951523", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get dc/rhpam7-rhpamcentr -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:21.209439", 
    "stderr": "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"rhpam7-rhpamcentr\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"rhpam7-rhpamcentr\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Set base param fact] ***************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:91
ok: [localhost] => {
    "ansible_facts": {
        "TEMPLATE_PARAMS": "-p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\""
    }, 
    "changed": false
}

TASK [ansible_openshift_rhpam : Set additional facts for non-trial environment] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:95
ok: [localhost] => {
    "ansible_facts": {
        "TEMPLATE_PARAMS": "-p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials'"
    }, 
    "changed": false
}

TASK [ansible_openshift_rhpam : Create PAM7 environment] ***********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:100
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166242.14-138478919519749 `" && echo ansible-tmp-1615166242.14-138478919519749="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166242.14-138478919519749 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpXIey39 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166242.14-138478919519749/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166242.14-138478919519749/ /opt/apb/.ansible/tmp/ansible-tmp-1615166242.14-138478919519749/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166242.14-138478919519749/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166242.14-138478919519749/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --template=rhpam79-authoring -p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials' -p IMAGE_STREAM_NAMESPACE=openshift -n rhpam-user2", 
    "delta": "0:00:01.384508", 
    "end": "2021-03-08 01:17:23.809273", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --template=rhpam79-authoring -p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials' -p IMAGE_STREAM_NAMESPACE=openshift -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:22.424765", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Deploying template \"openshift/rhpam79-authoring\" to project rhpam-user2\n\n     Red Hat Process Automation Manager 7.9 authoring environment (non-HA, persistent, with https)\n     ---------\n     Application template for a non-HA persistent authoring environment, for Red Hat Process Automation Manager 7.9 - Deprecated\n\n     A new persistent Process Automation Manager application have been created in your project.\n     The username/password needed for accessing the application are stored in \"rhpam-credentials\" secret as\n     KIE_ADMIN_USER and KIE_ADMIN_PWD\n     \n     You must create the secret named \"rhpam-credentials\" containing the KIE_ADMIN_USER and KIE_ADMIN_PWD values and the secrets named \"businesscentral-app-secret\" and \"kieserver-app-secret\"\n     containing the keystore.jks and keystore.jks files used for serving secure content.\n\n     * With parameters:\n        * Application Name=rhpam7\n        * Credentials secret=rhpam-credentials\n        * KIE Server Controller Token=\n        * KIE Server Bypass Auth User=false\n        * KIE Server Persistence DS=java:/jboss/datasources/rhpam\n        * KIE Server H2 Database User=sa\n        * KIE Server H2 Database Password=MDWHmI7! # generated\n        * KIE Server Mode=DEVELOPMENT\n        * KIE MBeans=enabled\n        * Drools Server Filter Classes=true\n        * Prometheus Server Extension Disabled=\n        * Business Central Custom http Route Hostname=\n        * Business Central Custom https Route Hostname=\n        * KIE Server Custom http Route Hostname=\n        * KIE Server Custom https Route Hostname=\n        * Business Central Server Keystore Secret Name=businesscentral-app-secret\n        * Business Central Server Keystore Filename=keystore.jks\n        * Business Central Server Certificate Name=jboss\n        * Business Central Server Keystore Password=mykeystorepass\n        * KIE Server Keystore Secret Name=kieserver-app-secret\n        * KIE Server Keystore Filename=keystore.jks\n        * KIE Server Certificate Name=jboss\n        * KIE Server Keystore Password=mykeystorepass\n        * Database Volume Capacity=1Gi\n        * Enable KIE server global discovery=false\n        * Prefer KIE Server OpenShift Service=true\n        * KIE ServerTemplate Cache TTL=5000\n        * ImageStream Namespace=openshift\n        * KIE Server ImageStream Name=rhpam-kieserver-rhel8\n        * ImageStream Tag=7.9.0\n        * Maven mirror URL=\n        * Maven mirror of=external:*,!repo-rhpamcentr\n        * Maven repository ID=repo-custom\n        * Maven repository URL=\n        * Maven repository user name=\n        * Maven repository password=\n        * Git hooks directory=\n        * Business Central Volume Capacity=1Gi\n        * Business Central Container Memory Limit=6Gi\n        * KIE Server Container Memory Limit=1Gi\n        * RH-SSO URL=\n        * RH-SSO Realm name=\n        * Business Central RH-SSO Client name=\n        * Business Central RH-SSO Client Secret=\n        * KIE Server RH-SSO Client name=\n        * KIE Server RH-SSO Client Secret=\n        * RH-SSO Realm admin user name=\n        * RH-SSO Realm Admin Password=\n        * RH-SSO Disable SSL Certificate Validation=false\n        * RH-SSO Principal Attribute=preferred_username\n        * LDAP Endpoint=\n        * LDAP Bind DN=\n        * LDAP Bind Credentials=\n        * LDAP JAAS Security Domain=\n        * LDAP Base DN=\n        * LDAP Base Search filter=\n        * LDAP Search scope=\n        * LDAP Search time limit=\n        * LDAP DN attribute=\n        * LDAP Parse username=\n        * LDAP Username begin string=\n        * LDAP Username end string=\n        * LDAP Role attributeID=\n        * LDAP Roles Search DN=\n        * LDAP Role search filter=\n        * LDAP Role recursion=\n        * LDAP Default role=\n        * LDAP Role name attribute ID=\n        * LDAP Role DN contains roleNameAttributeID=\n        * LDAP Role Attribute ID is DN=\n        * LDAP Referral user attribute ID=\n        * RoleMapping rolesProperties file path=\n        * RoleMapping replaceRole property=\n\n--> Creating resources ...\n    serviceaccount \"rhpam7-rhpamsvc\" created\n    rolebinding \"rhpam7-rhpamsvc-edit\" created\n    service \"rhpam7-rhpamcentr\" created\n    service \"rhpam7-kieserver\" created\n    route \"insecure-rhpam7-rhpamcentr\" created\n    route \"rhpam7-rhpamcentr\" created\n    route \"insecure-rhpam7-kieserver\" created\n    route \"rhpam7-kieserver\" created\n    deploymentconfig \"rhpam7-rhpamcentr\" created\n    deploymentconfig \"rhpam7-kieserver\" created\n    persistentvolumeclaim \"rhpam7-rhpamcentr-claim\" created\n    persistentvolumeclaim \"rhpam7-kie-claim\" created\n--> Success\n    Access your application via route 'insecure-rhpam7-rhpamcentr-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'rhpam7-rhpamcentr-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'insecure-rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Run 'oc status' to view your app.", 
    "stdout_lines": [
        "--> Deploying template \"openshift/rhpam79-authoring\" to project rhpam-user2", 
        "", 
        "     Red Hat Process Automation Manager 7.9 authoring environment (non-HA, persistent, with https)", 
        "     ---------", 
        "     Application template for a non-HA persistent authoring environment, for Red Hat Process Automation Manager 7.9 - Deprecated", 
        "", 
        "     A new persistent Process Automation Manager application have been created in your project.", 
        "     The username/password needed for accessing the application are stored in \"rhpam-credentials\" secret as", 
        "     KIE_ADMIN_USER and KIE_ADMIN_PWD", 
        "     ", 
        "     You must create the secret named \"rhpam-credentials\" containing the KIE_ADMIN_USER and KIE_ADMIN_PWD values and the secrets named \"businesscentral-app-secret\" and \"kieserver-app-secret\"", 
        "     containing the keystore.jks and keystore.jks files used for serving secure content.", 
        "", 
        "     * With parameters:", 
        "        * Application Name=rhpam7", 
        "        * Credentials secret=rhpam-credentials", 
        "        * KIE Server Controller Token=", 
        "        * KIE Server Bypass Auth User=false", 
        "        * KIE Server Persistence DS=java:/jboss/datasources/rhpam", 
        "        * KIE Server H2 Database User=sa", 
        "        * KIE Server H2 Database Password=MDWHmI7! # generated", 
        "        * KIE Server Mode=DEVELOPMENT", 
        "        * KIE MBeans=enabled", 
        "        * Drools Server Filter Classes=true", 
        "        * Prometheus Server Extension Disabled=", 
        "        * Business Central Custom http Route Hostname=", 
        "        * Business Central Custom https Route Hostname=", 
        "        * KIE Server Custom http Route Hostname=", 
        "        * KIE Server Custom https Route Hostname=", 
        "        * Business Central Server Keystore Secret Name=businesscentral-app-secret", 
        "        * Business Central Server Keystore Filename=keystore.jks", 
        "        * Business Central Server Certificate Name=jboss", 
        "        * Business Central Server Keystore Password=mykeystorepass", 
        "        * KIE Server Keystore Secret Name=kieserver-app-secret", 
        "        * KIE Server Keystore Filename=keystore.jks", 
        "        * KIE Server Certificate Name=jboss", 
        "        * KIE Server Keystore Password=mykeystorepass", 
        "        * Database Volume Capacity=1Gi", 
        "        * Enable KIE server global discovery=false", 
        "        * Prefer KIE Server OpenShift Service=true", 
        "        * KIE ServerTemplate Cache TTL=5000", 
        "        * ImageStream Namespace=openshift", 
        "        * KIE Server ImageStream Name=rhpam-kieserver-rhel8", 
        "        * ImageStream Tag=7.9.0", 
        "        * Maven mirror URL=", 
        "        * Maven mirror of=external:*,!repo-rhpamcentr", 
        "        * Maven repository ID=repo-custom", 
        "        * Maven repository URL=", 
        "        * Maven repository user name=", 
        "        * Maven repository password=", 
        "        * Git hooks directory=", 
        "        * Business Central Volume Capacity=1Gi", 
        "        * Business Central Container Memory Limit=6Gi", 
        "        * KIE Server Container Memory Limit=1Gi", 
        "        * RH-SSO URL=", 
        "        * RH-SSO Realm name=", 
        "        * Business Central RH-SSO Client name=", 
        "        * Business Central RH-SSO Client Secret=", 
        "        * KIE Server RH-SSO Client name=", 
        "        * KIE Server RH-SSO Client Secret=", 
        "        * RH-SSO Realm admin user name=", 
        "        * RH-SSO Realm Admin Password=", 
        "        * RH-SSO Disable SSL Certificate Validation=false", 
        "        * RH-SSO Principal Attribute=preferred_username", 
        "        * LDAP Endpoint=", 
        "        * LDAP Bind DN=", 
        "        * LDAP Bind Credentials=", 
        "        * LDAP JAAS Security Domain=", 
        "        * LDAP Base DN=", 
        "        * LDAP Base Search filter=", 
        "        * LDAP Search scope=", 
        "        * LDAP Search time limit=", 
        "        * LDAP DN attribute=", 
        "        * LDAP Parse username=", 
        "        * LDAP Username begin string=", 
        "        * LDAP Username end string=", 
        "        * LDAP Role attributeID=", 
        "        * LDAP Roles Search DN=", 
        "        * LDAP Role search filter=", 
        "        * LDAP Role recursion=", 
        "        * LDAP Default role=", 
        "        * LDAP Role name attribute ID=", 
        "        * LDAP Role DN contains roleNameAttributeID=", 
        "        * LDAP Role Attribute ID is DN=", 
        "        * LDAP Referral user attribute ID=", 
        "        * RoleMapping rolesProperties file path=", 
        "        * RoleMapping replaceRole property=", 
        "", 
        "--> Creating resources ...", 
        "    serviceaccount \"rhpam7-rhpamsvc\" created", 
        "    rolebinding \"rhpam7-rhpamsvc-edit\" created", 
        "    service \"rhpam7-rhpamcentr\" created", 
        "    service \"rhpam7-kieserver\" created", 
        "    route \"insecure-rhpam7-rhpamcentr\" created", 
        "    route \"rhpam7-rhpamcentr\" created", 
        "    route \"insecure-rhpam7-kieserver\" created", 
        "    route \"rhpam7-kieserver\" created", 
        "    deploymentconfig \"rhpam7-rhpamcentr\" created", 
        "    deploymentconfig \"rhpam7-kieserver\" created", 
        "    persistentvolumeclaim \"rhpam7-rhpamcentr-claim\" created", 
        "    persistentvolumeclaim \"rhpam7-kie-claim\" created", 
        "--> Success", 
        "    Access your application via route 'insecure-rhpam7-rhpamcentr-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'rhpam7-rhpamcentr-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'insecure-rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Run 'oc status' to view your app."
    ]
}

## 繰り返し(USER3) 
TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:3
ok: [localhost] => {
    "msg": [
        "Openshift project", 
        "-> Check if rhpam-user3 project exists"
    ]
}

TASK [ansible_openshift_rhpam : check if rhpam-user3 project exists] ***********
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:8
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166243.94-232563167961325 `" && echo ansible-tmp-1615166243.94-232563167961325="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166243.94-232563167961325 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpcy5_T0 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166243.94-232563167961325/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166243.94-232563167961325/ /opt/apb/.ansible/tmp/ansible-tmp-1615166243.94-232563167961325/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166243.94-232563167961325/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166243.94-232563167961325/ > /dev/null 2>&1 && sleep 0'
ok: [localhost] => {
    "changed": false, 
    "cmd": "oc get project rhpam-user3", 
    "delta": "0:00:00.816303", 
    "end": "2021-03-08 01:17:25.043254", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get project rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:24.226951", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "NAME          DISPLAY NAME           STATUS\nrhpam-user3   RHPAM 7.9.0 - User 3   Active", 
    "stdout_lines": [
        "NAME          DISPLAY NAME           STATUS", 
        "rhpam-user3   RHPAM 7.9.0 - User 3   Active"
    ]
}

TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:14
ok: [localhost] => {
    "msg": [
        "Openshift project", 
        "-> Create Openshift project (rhpam-user3)"
    ]
}

TASK [ansible_openshift_rhpam : create rhpam-user3 project] ********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:19
skipping: [localhost] => {
    "changed": false, 
    "skip_reason": "Conditional result was False"
}

TASK [ansible_openshift_rhpam : debug] *****************************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:26
ok: [localhost] => {
    "msg": "-> Process RHPAM Template"
}

TASK [ansible_openshift_rhpam : Check Secrets Business Central] ****************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:29
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166245.32-37769316152879 `" && echo ansible-tmp-1615166245.32-37769316152879="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166245.32-37769316152879 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpS2mc4c TO /opt/apb/.ansible/tmp/ansible-tmp-1615166245.32-37769316152879/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166245.32-37769316152879/ /opt/apb/.ansible/tmp/ansible-tmp-1615166245.32-37769316152879/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166245.32-37769316152879/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166245.32-37769316152879/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/businesscentral-app-secret -n rhpam-user3", 
    "delta": "0:00:00.817294", 
    "end": "2021-03-08 01:17:26.426306", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/businesscentral-app-secret -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:25.609012", 
    "stderr": "Error from server (NotFound): secrets \"businesscentral-app-secret\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"businesscentral-app-secret\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Create Secrets Business Central] ***************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:35
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166246.52-207191749976457 `" && echo ansible-tmp-1615166246.52-207191749976457="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166246.52-207191749976457 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpCHqEJ4 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166246.52-207191749976457/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166246.52-207191749976457/ /opt/apb/.ansible/tmp/ansible-tmp-1615166246.52-207191749976457/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166246.52-207191749976457/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166246.52-207191749976457/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=businesscentral-app-secret | oc create -f - -n rhpam-user3", 
    "delta": "0:00:01.426717", 
    "end": "2021-03-08 01:17:28.233964", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=businesscentral-app-secret | oc create -f - -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:26.807247", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"businesscentral-app-secret\" created", 
    "stdout_lines": [
        "secret \"businesscentral-app-secret\" created"
    ]
}

TASK [ansible_openshift_rhpam : Check Secrets KIE-Server] **********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:39
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166248.33-242074609299791 `" && echo ansible-tmp-1615166248.33-242074609299791="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166248.33-242074609299791 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpJaNEoe TO /opt/apb/.ansible/tmp/ansible-tmp-1615166248.33-242074609299791/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166248.33-242074609299791/ /opt/apb/.ansible/tmp/ansible-tmp-1615166248.33-242074609299791/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166248.33-242074609299791/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166248.33-242074609299791/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/kieserver-app-secret -n rhpam-user3", 
    "delta": "0:00:00.754024", 
    "end": "2021-03-08 01:17:29.368688", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/kieserver-app-secret -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:28.614664", 
    "stderr": "Error from server (NotFound): secrets \"kieserver-app-secret\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"kieserver-app-secret\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Create Secrets KIE-server] *********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:45
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166249.44-215716029198181 `" && echo ansible-tmp-1615166249.44-215716029198181="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166249.44-215716029198181 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpPLVFC5 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166249.44-215716029198181/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166249.44-215716029198181/ /opt/apb/.ansible/tmp/ansible-tmp-1615166249.44-215716029198181/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166249.44-215716029198181/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166249.44-215716029198181/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=kieserver-app-secret | oc create -f - -n rhpam-user3", 
    "delta": "0:00:01.412173", 
    "end": "2021-03-08 01:17:31.140099", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc process -f https://raw.githubusercontent.com/jboss-container-images/rhpam-7-openshift-image/7.9.x/example-app-secret-template.yaml -p SECRET_NAME=kieserver-app-secret | oc create -f - -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:29.727926", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"kieserver-app-secret\" created", 
    "stdout_lines": [
        "secret \"kieserver-app-secret\" created"
    ]
}

TASK [ansible_openshift_rhpam : Check Generic Secret with RHPAM Credentials] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:49
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166251.23-56546004769236 `" && echo ansible-tmp-1615166251.23-56546004769236="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166251.23-56546004769236 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpOjLpSF TO /opt/apb/.ansible/tmp/ansible-tmp-1615166251.23-56546004769236/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166251.23-56546004769236/ /opt/apb/.ansible/tmp/ansible-tmp-1615166251.23-56546004769236/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166251.23-56546004769236/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166251.23-56546004769236/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get secret/rhpam-credentials -n rhpam-user3", 
    "delta": "0:00:00.823549", 
    "end": "2021-03-08 01:17:32.328881", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get secret/rhpam-credentials -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:31.505332", 
    "stderr": "Error from server (NotFound): secrets \"rhpam-credentials\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): secrets \"rhpam-credentials\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Create Generic Secret with RHPAM Credentials] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:55
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166252.42-239891247775089 `" && echo ansible-tmp-1615166252.42-239891247775089="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166252.42-239891247775089 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp29zaU8 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166252.42-239891247775089/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166252.42-239891247775089/ /opt/apb/.ansible/tmp/ansible-tmp-1615166252.42-239891247775089/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166252.42-239891247775089/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166252.42-239891247775089/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create secret generic rhpam-credentials --from-literal=KIE_ADMIN_USER=pamAdmin --from-literal=KIE_ADMIN_PWD=redhatpam1! -n rhpam-user3", 
    "delta": "0:00:00.794842", 
    "end": "2021-03-08 01:17:33.444187", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create secret generic rhpam-credentials --from-literal=KIE_ADMIN_USER=pamAdmin --from-literal=KIE_ADMIN_PWD=redhatpam1! -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:32.649345", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "secret \"rhpam-credentials\" created", 
    "stdout_lines": [
        "secret \"rhpam-credentials\" created"
    ]
}

TASK [ansible_openshift_rhpam : check if RHPAM exists] *************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:85
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166253.52-241743184816079 `" && echo ansible-tmp-1615166253.52-241743184816079="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166253.52-241743184816079 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp5iA0nA TO /opt/apb/.ansible/tmp/ansible-tmp-1615166253.52-241743184816079/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166253.52-241743184816079/ /opt/apb/.ansible/tmp/ansible-tmp-1615166253.52-241743184816079/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166253.52-241743184816079/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166253.52-241743184816079/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get dc/rhpam7-rhpamcentr -n rhpam-user3", 
    "delta": "0:00:00.754074", 
    "end": "2021-03-08 01:17:34.555719", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get dc/rhpam7-rhpamcentr -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:33.801645", 
    "stderr": "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"rhpam7-rhpamcentr\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"rhpam7-rhpamcentr\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [ansible_openshift_rhpam : Set base param fact] ***************************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:91
ok: [localhost] => {
    "ansible_facts": {
        "TEMPLATE_PARAMS": "-p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\""
    }, 
    "changed": false
}

TASK [ansible_openshift_rhpam : Set additional facts for non-trial environment] ***
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:95
ok: [localhost] => {
    "ansible_facts": {
        "TEMPLATE_PARAMS": "-p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials'"
    }, 
    "changed": false
}

TASK [ansible_openshift_rhpam : Create PAM7 environment] ***********************
task path: /etc/ansible/roles/ansible_openshift_rhpam/tasks/main.yml:100
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166254.75-163613644744713 `" && echo ansible-tmp-1615166254.75-163613644744713="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166254.75-163613644744713 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpNmLYUj TO /opt/apb/.ansible/tmp/ansible-tmp-1615166254.75-163613644744713/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166254.75-163613644744713/ /opt/apb/.ansible/tmp/ansible-tmp-1615166254.75-163613644744713/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166254.75-163613644744713/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166254.75-163613644744713/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app --template=rhpam79-authoring -p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials' -p IMAGE_STREAM_NAMESPACE=openshift -n rhpam-user3", 
    "delta": "0:00:01.343907", 
    "end": "2021-03-08 01:17:36.371675", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app --template=rhpam79-authoring -p APPLICATION_NAME=\"rhpam7\" -p BUSINESS_CENTRAL_MEMORY_LIMIT=\"6Gi\" -p BUSINESS_CENTRAL_HTTPS_SECRET='businesscentral-app-secret' -p KIE_SERVER_HTTPS_SECRET='kieserver-app-secret' -p CREDENTIALS_SECRET='rhpam-credentials' -p IMAGE_STREAM_NAMESPACE=openshift -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:35.027768", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Deploying template \"openshift/rhpam79-authoring\" to project rhpam-user3\n\n     Red Hat Process Automation Manager 7.9 authoring environment (non-HA, persistent, with https)\n     ---------\n     Application template for a non-HA persistent authoring environment, for Red Hat Process Automation Manager 7.9 - Deprecated\n\n     A new persistent Process Automation Manager application have been created in your project.\n     The username/password needed for accessing the application are stored in \"rhpam-credentials\" secret as\n     KIE_ADMIN_USER and KIE_ADMIN_PWD\n     \n     You must create the secret named \"rhpam-credentials\" containing the KIE_ADMIN_USER and KIE_ADMIN_PWD values and the secrets named \"businesscentral-app-secret\" and \"kieserver-app-secret\"\n     containing the keystore.jks and keystore.jks files used for serving secure content.\n\n     * With parameters:\n        * Application Name=rhpam7\n        * Credentials secret=rhpam-credentials\n        * KIE Server Controller Token=\n        * KIE Server Bypass Auth User=false\n        * KIE Server Persistence DS=java:/jboss/datasources/rhpam\n        * KIE Server H2 Database User=sa\n        * KIE Server H2 Database Password=SyRDIU1! # generated\n        * KIE Server Mode=DEVELOPMENT\n        * KIE MBeans=enabled\n        * Drools Server Filter Classes=true\n        * Prometheus Server Extension Disabled=\n        * Business Central Custom http Route Hostname=\n        * Business Central Custom https Route Hostname=\n        * KIE Server Custom http Route Hostname=\n        * KIE Server Custom https Route Hostname=\n        * Business Central Server Keystore Secret Name=businesscentral-app-secret\n        * Business Central Server Keystore Filename=keystore.jks\n        * Business Central Server Certificate Name=jboss\n        * Business Central Server Keystore Password=mykeystorepass\n        * KIE Server Keystore Secret Name=kieserver-app-secret\n        * KIE Server Keystore Filename=keystore.jks\n        * KIE Server Certificate Name=jboss\n        * KIE Server Keystore Password=mykeystorepass\n        * Database Volume Capacity=1Gi\n        * Enable KIE server global discovery=false\n        * Prefer KIE Server OpenShift Service=true\n        * KIE ServerTemplate Cache TTL=5000\n        * ImageStream Namespace=openshift\n        * KIE Server ImageStream Name=rhpam-kieserver-rhel8\n        * ImageStream Tag=7.9.0\n        * Maven mirror URL=\n        * Maven mirror of=external:*,!repo-rhpamcentr\n        * Maven repository ID=repo-custom\n        * Maven repository URL=\n        * Maven repository user name=\n        * Maven repository password=\n        * Git hooks directory=\n        * Business Central Volume Capacity=1Gi\n        * Business Central Container Memory Limit=6Gi\n        * KIE Server Container Memory Limit=1Gi\n        * RH-SSO URL=\n        * RH-SSO Realm name=\n        * Business Central RH-SSO Client name=\n        * Business Central RH-SSO Client Secret=\n        * KIE Server RH-SSO Client name=\n        * KIE Server RH-SSO Client Secret=\n        * RH-SSO Realm admin user name=\n        * RH-SSO Realm Admin Password=\n        * RH-SSO Disable SSL Certificate Validation=false\n        * RH-SSO Principal Attribute=preferred_username\n        * LDAP Endpoint=\n        * LDAP Bind DN=\n        * LDAP Bind Credentials=\n        * LDAP JAAS Security Domain=\n        * LDAP Base DN=\n        * LDAP Base Search filter=\n        * LDAP Search scope=\n        * LDAP Search time limit=\n        * LDAP DN attribute=\n        * LDAP Parse username=\n        * LDAP Username begin string=\n        * LDAP Username end string=\n        * LDAP Role attributeID=\n        * LDAP Roles Search DN=\n        * LDAP Role search filter=\n        * LDAP Role recursion=\n        * LDAP Default role=\n        * LDAP Role name attribute ID=\n        * LDAP Role DN contains roleNameAttributeID=\n        * LDAP Role Attribute ID is DN=\n        * LDAP Referral user attribute ID=\n        * RoleMapping rolesProperties file path=\n        * RoleMapping replaceRole property=\n\n--> Creating resources ...\n    serviceaccount \"rhpam7-rhpamsvc\" created\n    rolebinding \"rhpam7-rhpamsvc-edit\" created\n    service \"rhpam7-rhpamcentr\" created\n    service \"rhpam7-kieserver\" created\n    route \"insecure-rhpam7-rhpamcentr\" created\n    route \"rhpam7-rhpamcentr\" created\n    route \"insecure-rhpam7-kieserver\" created\n    route \"rhpam7-kieserver\" created\n    deploymentconfig \"rhpam7-rhpamcentr\" created\n    deploymentconfig \"rhpam7-kieserver\" created\n    persistentvolumeclaim \"rhpam7-rhpamcentr-claim\" created\n    persistentvolumeclaim \"rhpam7-kie-claim\" created\n--> Success\n    Access your application via route 'insecure-rhpam7-rhpamcentr-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'rhpam7-rhpamcentr-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'insecure-rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Access your application via route 'rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Run 'oc status' to view your app.", 
    "stdout_lines": [
        "--> Deploying template \"openshift/rhpam79-authoring\" to project rhpam-user3", 
        "", 
        "     Red Hat Process Automation Manager 7.9 authoring environment (non-HA, persistent, with https)", 
        "     ---------", 
        "     Application template for a non-HA persistent authoring environment, for Red Hat Process Automation Manager 7.9 - Deprecated", 
        "", 
        "     A new persistent Process Automation Manager application have been created in your project.", 
        "     The username/password needed for accessing the application are stored in \"rhpam-credentials\" secret as", 
        "     KIE_ADMIN_USER and KIE_ADMIN_PWD", 
        "     ", 
        "     You must create the secret named \"rhpam-credentials\" containing the KIE_ADMIN_USER and KIE_ADMIN_PWD values and the secrets named \"businesscentral-app-secret\" and \"kieserver-app-secret\"", 
        "     containing the keystore.jks and keystore.jks files used for serving secure content.", 
        "", 
        "     * With parameters:", 
        "        * Application Name=rhpam7", 
        "        * Credentials secret=rhpam-credentials", 
        "        * KIE Server Controller Token=", 
        "        * KIE Server Bypass Auth User=false", 
        "        * KIE Server Persistence DS=java:/jboss/datasources/rhpam", 
        "        * KIE Server H2 Database User=sa", 
        "        * KIE Server H2 Database Password=SyRDIU1! # generated", 
        "        * KIE Server Mode=DEVELOPMENT", 
        "        * KIE MBeans=enabled", 
        "        * Drools Server Filter Classes=true", 
        "        * Prometheus Server Extension Disabled=", 
        "        * Business Central Custom http Route Hostname=", 
        "        * Business Central Custom https Route Hostname=", 
        "        * KIE Server Custom http Route Hostname=", 
        "        * KIE Server Custom https Route Hostname=", 
        "        * Business Central Server Keystore Secret Name=businesscentral-app-secret", 
        "        * Business Central Server Keystore Filename=keystore.jks", 
        "        * Business Central Server Certificate Name=jboss", 
        "        * Business Central Server Keystore Password=mykeystorepass", 
        "        * KIE Server Keystore Secret Name=kieserver-app-secret", 
        "        * KIE Server Keystore Filename=keystore.jks", 
        "        * KIE Server Certificate Name=jboss", 
        "        * KIE Server Keystore Password=mykeystorepass", 
        "        * Database Volume Capacity=1Gi", 
        "        * Enable KIE server global discovery=false", 
        "        * Prefer KIE Server OpenShift Service=true", 
        "        * KIE ServerTemplate Cache TTL=5000", 
        "        * ImageStream Namespace=openshift", 
        "        * KIE Server ImageStream Name=rhpam-kieserver-rhel8", 
        "        * ImageStream Tag=7.9.0", 
        "        * Maven mirror URL=", 
        "        * Maven mirror of=external:*,!repo-rhpamcentr", 
        "        * Maven repository ID=repo-custom", 
        "        * Maven repository URL=", 
        "        * Maven repository user name=", 
        "        * Maven repository password=", 
        "        * Git hooks directory=", 
        "        * Business Central Volume Capacity=1Gi", 
        "        * Business Central Container Memory Limit=6Gi", 
        "        * KIE Server Container Memory Limit=1Gi", 
        "        * RH-SSO URL=", 
        "        * RH-SSO Realm name=", 
        "        * Business Central RH-SSO Client name=", 
        "        * Business Central RH-SSO Client Secret=", 
        "        * KIE Server RH-SSO Client name=", 
        "        * KIE Server RH-SSO Client Secret=", 
        "        * RH-SSO Realm admin user name=", 
        "        * RH-SSO Realm Admin Password=", 
        "        * RH-SSO Disable SSL Certificate Validation=false", 
        "        * RH-SSO Principal Attribute=preferred_username", 
        "        * LDAP Endpoint=", 
        "        * LDAP Bind DN=", 
        "        * LDAP Bind Credentials=", 
        "        * LDAP JAAS Security Domain=", 
        "        * LDAP Base DN=", 
        "        * LDAP Base Search filter=", 
        "        * LDAP Search scope=", 
        "        * LDAP Search time limit=", 
        "        * LDAP DN attribute=", 
        "        * LDAP Parse username=", 
        "        * LDAP Username begin string=", 
        "        * LDAP Username end string=", 
        "        * LDAP Role attributeID=", 
        "        * LDAP Roles Search DN=", 
        "        * LDAP Role search filter=", 
        "        * LDAP Role recursion=", 
        "        * LDAP Default role=", 
        "        * LDAP Role name attribute ID=", 
        "        * LDAP Role DN contains roleNameAttributeID=", 
        "        * LDAP Role Attribute ID is DN=", 
        "        * LDAP Referral user attribute ID=", 
        "        * RoleMapping rolesProperties file path=", 
        "        * RoleMapping replaceRole property=", 
        "", 
        "--> Creating resources ...", 
        "    serviceaccount \"rhpam7-rhpamsvc\" created", 
        "    rolebinding \"rhpam7-rhpamsvc-edit\" created", 
        "    service \"rhpam7-rhpamcentr\" created", 
        "    service \"rhpam7-kieserver\" created", 
        "    route \"insecure-rhpam7-rhpamcentr\" created", 
        "    route \"rhpam7-rhpamcentr\" created", 
        "    route \"insecure-rhpam7-kieserver\" created", 
        "    route \"rhpam7-kieserver\" created", 
        "    deploymentconfig \"rhpam7-rhpamcentr\" created", 
        "    deploymentconfig \"rhpam7-kieserver\" created", 
        "    persistentvolumeclaim \"rhpam7-rhpamcentr-claim\" created", 
        "    persistentvolumeclaim \"rhpam7-kie-claim\" created", 
        "--> Success", 
        "    Access your application via route 'insecure-rhpam7-rhpamcentr-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'rhpam7-rhpamcentr-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'insecure-rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Access your application via route 'rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Run 'oc status' to view your app."
    ]
}

## ここまで

# rhpac_bc
TASK [include_role] ************************************************************
task path: /opt/apb/actions/provision.yml:248

## rhpam_bc : Configure Liveness probe
TASK [rhpam_bc : Configure Liveness probe] *************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166256.93-192393704129586 `" && echo ansible-tmp-1615166256.93-192393704129586="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166256.93-192393704129586 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp57AstL TO /opt/apb/.ansible/tmp/ansible-tmp-1615166256.93-192393704129586/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166256.93-192393704129586/ /opt/apb/.ansible/tmp/ansible-tmp-1615166256.93-192393704129586/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166256.93-192393704129586/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166256.93-192393704129586/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/rhpam7-rhpamcentr --liveness --initial-delay-seconds=360 -n rhpam-user1", 
    "delta": "0:00:00.810055", 
    "end": "2021-03-08 01:17:38.027435", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/rhpam7-rhpamcentr --liveness --initial-delay-seconds=360 -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:37.217380", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## rhpam_bc : Configure Readiness probe
TASK [rhpam_bc : Configure Readiness probe] ************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:6
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166258.11-150079998344700 `" && echo ansible-tmp-1615166258.11-150079998344700="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166258.11-150079998344700 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpmz7ZE7 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166258.11-150079998344700/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166258.11-150079998344700/ /opt/apb/.ansible/tmp/ansible-tmp-1615166258.11-150079998344700/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166258.11-150079998344700/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166258.11-150079998344700/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/rhpam7-rhpamcentr --readiness --initial-delay-seconds=90 -n rhpam-user1", 
    "delta": "0:00:00.779306", 
    "end": "2021-03-08 01:17:39.123725", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/rhpam7-rhpamcentr --readiness --initial-delay-seconds=90 -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:38.344419", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## rhpam_bc : Set KIE_ADMIN Password
TASK [rhpam_bc : Set KIE_ADMIN Password] ***************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166259.21-67779588357927 `" && echo ansible-tmp-1615166259.21-67779588357927="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166259.21-67779588357927 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpjigShI TO /opt/apb/.ansible/tmp/ansible-tmp-1615166259.21-67779588357927/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166259.21-67779588357927/ /opt/apb/.ansible/tmp/ansible-tmp-1615166259.21-67779588357927/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166259.21-67779588357927/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166259.21-67779588357927/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_ADMIN_PWD=redhatpam1! -n rhpam-user1", 
    "delta": "0:00:00.790650", 
    "end": "2021-03-08 01:17:40.228476", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_ADMIN_PWD=redhatpam1! -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:39.437826", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## rhpam_bc : Set KIE_SERVER_CONTROLLER Password
TASK [rhpam_bc : Set KIE_SERVER_CONTROLLER Password] ***************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:12
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166260.33-93887932412469 `" && echo ansible-tmp-1615166260.33-93887932412469="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166260.33-93887932412469 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp3Fgu4P TO /opt/apb/.ansible/tmp/ansible-tmp-1615166260.33-93887932412469/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166260.33-93887932412469/ /opt/apb/.ansible/tmp/ansible-tmp-1615166260.33-93887932412469/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166260.33-93887932412469/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166260.33-93887932412469/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_CONTROLLER_PWD=test1234! -n rhpam-user1", 
    "delta": "0:00:00.795469", 
    "end": "2021-03-08 01:17:41.409583", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_CONTROLLER_PWD=test1234! -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:40.614114", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## rhpam_bc : Set KIE_SERVER Password
TASK [rhpam_bc : Set KIE_SERVER Password] **************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:15
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166261.51-269538145620893 `" && echo ansible-tmp-1615166261.51-269538145620893="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166261.51-269538145620893 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpADet7g TO /opt/apb/.ansible/tmp/ansible-tmp-1615166261.51-269538145620893/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166261.51-269538145620893/ /opt/apb/.ansible/tmp/ansible-tmp-1615166261.51-269538145620893/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166261.51-269538145620893/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166261.51-269538145620893/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_PWD=test1234! -n rhpam-user1", 
    "delta": "0:00:00.825201", 
    "end": "2021-03-08 01:17:42.562250", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_PWD=test1234! -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:41.737049", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## 繰り返し (USER2)
TASK [rhpam_bc : Configure Liveness probe] *************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166262.62-55437250707512 `" && echo ansible-tmp-1615166262.62-55437250707512="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166262.62-55437250707512 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpIe1K10 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166262.62-55437250707512/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166262.62-55437250707512/ /opt/apb/.ansible/tmp/ansible-tmp-1615166262.62-55437250707512/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166262.62-55437250707512/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166262.62-55437250707512/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/rhpam7-rhpamcentr --liveness --initial-delay-seconds=360 -n rhpam-user2", 
    "delta": "0:00:00.795891", 
    "end": "2021-03-08 01:17:43.699127", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/rhpam7-rhpamcentr --liveness --initial-delay-seconds=360 -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:42.903236", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Configure Readiness probe] ************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:6
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166263.75-279082882225865 `" && echo ansible-tmp-1615166263.75-279082882225865="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166263.75-279082882225865 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpzpPK_M TO /opt/apb/.ansible/tmp/ansible-tmp-1615166263.75-279082882225865/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166263.75-279082882225865/ /opt/apb/.ansible/tmp/ansible-tmp-1615166263.75-279082882225865/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166263.75-279082882225865/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166263.75-279082882225865/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/rhpam7-rhpamcentr --readiness --initial-delay-seconds=90 -n rhpam-user2", 
    "delta": "0:00:00.833686", 
    "end": "2021-03-08 01:17:44.857007", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/rhpam7-rhpamcentr --readiness --initial-delay-seconds=90 -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:44.023321", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Set KIE_ADMIN Password] ***************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166264.92-53419792156207 `" && echo ansible-tmp-1615166264.92-53419792156207="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166264.92-53419792156207 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpYpKV0i TO /opt/apb/.ansible/tmp/ansible-tmp-1615166264.92-53419792156207/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166264.92-53419792156207/ /opt/apb/.ansible/tmp/ansible-tmp-1615166264.92-53419792156207/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166264.92-53419792156207/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166264.92-53419792156207/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_ADMIN_PWD=redhatpam1! -n rhpam-user2", 
    "delta": "0:00:00.807426", 
    "end": "2021-03-08 01:17:45.954171", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_ADMIN_PWD=redhatpam1! -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:45.146745", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Set KIE_SERVER_CONTROLLER Password] ***************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:12
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166266.03-122990375334791 `" && echo ansible-tmp-1615166266.03-122990375334791="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166266.03-122990375334791 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpwtKLAE TO /opt/apb/.ansible/tmp/ansible-tmp-1615166266.03-122990375334791/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166266.03-122990375334791/ /opt/apb/.ansible/tmp/ansible-tmp-1615166266.03-122990375334791/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166266.03-122990375334791/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166266.03-122990375334791/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_CONTROLLER_PWD=test1234! -n rhpam-user2", 
    "delta": "0:00:00.760550", 
    "end": "2021-03-08 01:17:47.074330", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_CONTROLLER_PWD=test1234! -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:46.313780", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Set KIE_SERVER Password] **************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:15
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166267.14-49784757979546 `" && echo ansible-tmp-1615166267.14-49784757979546="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166267.14-49784757979546 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp74Ez8P TO /opt/apb/.ansible/tmp/ansible-tmp-1615166267.14-49784757979546/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166267.14-49784757979546/ /opt/apb/.ansible/tmp/ansible-tmp-1615166267.14-49784757979546/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166267.14-49784757979546/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166267.14-49784757979546/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_PWD=test1234! -n rhpam-user2", 
    "delta": "0:00:00.779082", 
    "end": "2021-03-08 01:17:48.203165", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_PWD=test1234! -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:47.424083", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## ## 繰り返し (USER3)
TASK [rhpam_bc : Configure Liveness probe] *************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166268.3-269213419826893 `" && echo ansible-tmp-1615166268.3-269213419826893="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166268.3-269213419826893 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpX0fZTX TO /opt/apb/.ansible/tmp/ansible-tmp-1615166268.3-269213419826893/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166268.3-269213419826893/ /opt/apb/.ansible/tmp/ansible-tmp-1615166268.3-269213419826893/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166268.3-269213419826893/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166268.3-269213419826893/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/rhpam7-rhpamcentr --liveness --initial-delay-seconds=360 -n rhpam-user3", 
    "delta": "0:00:00.792606", 
    "end": "2021-03-08 01:17:49.328201", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/rhpam7-rhpamcentr --liveness --initial-delay-seconds=360 -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:48.535595", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Configure Readiness probe] ************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:6
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166269.41-132012592860261 `" && echo ansible-tmp-1615166269.41-132012592860261="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166269.41-132012592860261 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp1gLSHI TO /opt/apb/.ansible/tmp/ansible-tmp-1615166269.41-132012592860261/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166269.41-132012592860261/ /opt/apb/.ansible/tmp/ansible-tmp-1615166269.41-132012592860261/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166269.41-132012592860261/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166269.41-132012592860261/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set probe dc/rhpam7-rhpamcentr --readiness --initial-delay-seconds=90 -n rhpam-user3", 
    "delta": "0:00:00.807531", 
    "end": "2021-03-08 01:17:50.451596", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set probe dc/rhpam7-rhpamcentr --readiness --initial-delay-seconds=90 -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:49.644065", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Set KIE_ADMIN Password] ***************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166270.53-119025899180885 `" && echo ansible-tmp-1615166270.53-119025899180885="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166270.53-119025899180885 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp6sA454 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166270.53-119025899180885/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166270.53-119025899180885/ /opt/apb/.ansible/tmp/ansible-tmp-1615166270.53-119025899180885/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166270.53-119025899180885/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166270.53-119025899180885/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_ADMIN_PWD=redhatpam1! -n rhpam-user3", 
    "delta": "0:00:00.793012", 
    "end": "2021-03-08 01:17:51.603134", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_ADMIN_PWD=redhatpam1! -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:50.810122", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Set KIE_SERVER_CONTROLLER Password] ***************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:12
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166271.7-185786596681800 `" && echo ansible-tmp-1615166271.7-185786596681800="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166271.7-185786596681800 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmppF3eKR TO /opt/apb/.ansible/tmp/ansible-tmp-1615166271.7-185786596681800/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166271.7-185786596681800/ /opt/apb/.ansible/tmp/ansible-tmp-1615166271.7-185786596681800/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166271.7-185786596681800/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166271.7-185786596681800/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_CONTROLLER_PWD=test1234! -n rhpam-user3", 
    "delta": "0:00:00.820444", 
    "end": "2021-03-08 01:17:52.757044", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_CONTROLLER_PWD=test1234! -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:51.936600", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

TASK [rhpam_bc : Set KIE_SERVER Password] **************************************
task path: /opt/ansible/roles/rhpam_bc/tasks/main.yml:15
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166272.82-96739073401485 `" && echo ansible-tmp-1615166272.82-96739073401485="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166272.82-96739073401485 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpGwVzPQ TO /opt/apb/.ansible/tmp/ansible-tmp-1615166272.82-96739073401485/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166272.82-96739073401485/ /opt/apb/.ansible/tmp/ansible-tmp-1615166272.82-96739073401485/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166272.82-96739073401485/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166272.82-96739073401485/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_PWD=test1234! -n rhpam-user3", 
    "delta": "0:00:00.792157", 
    "end": "2021-03-08 01:17:53.836646", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr KIE_SERVER_PWD=test1234! -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:53.044489", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

# ここまで rhpam_bc

# rhpam_bc_cm_showcase
TASK [include_role] ************************************************************
task path: /opt/apb/actions/provision.yml:254

## rhpam_bc_cm_showcase : Check if ImageStream exists
TASK [rhpam_bc_cm_showcase : Check if ImageStream exists] **********************
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166274.51-16194134081035 `" && echo ansible-tmp-1615166274.51-16194134081035="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166274.51-16194134081035 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpUTYBar TO /opt/apb/.ansible/tmp/ansible-tmp-1615166274.51-16194134081035/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166274.51-16194134081035/ /opt/apb/.ansible/tmp/ansible-tmp-1615166274.51-16194134081035/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166274.51-16194134081035/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166274.51-16194134081035/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get is/rhpam-businesscentral-rhel8-cm-showcase -n rhpam-user1", 
    "delta": "0:00:00.802485", 
    "end": "2021-03-08 01:17:55.550332", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is/rhpam-businesscentral-rhel8-cm-showcase -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:17:54.747847", 
    "stderr": "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## rhpam_bc_cm_showcase : Create ImageStream
TASK [rhpam_bc_cm_showcase : Create ImageStream] *******************************
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166275.63-10900773799975 `" && echo ansible-tmp-1615166275.63-10900773799975="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166275.63-10900773799975 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmptU8yVj TO /opt/apb/.ansible/tmp/ansible-tmp-1615166275.63-10900773799975/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166275.63-10900773799975/ /opt/apb/.ansible/tmp/ansible-tmp-1615166275.63-10900773799975/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166275.63-10900773799975/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166275.63-10900773799975/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create -f /opt/ansible/roles/rhpam_bc_cm_showcase/files/rhpam79-bc-cm-image-streams.yml -n rhpam-user1", 
    "delta": "0:00:00.835426", 
    "end": "2021-03-08 01:17:56.749823", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create -f /opt/ansible/roles/rhpam_bc_cm_showcase/files/rhpam79-bc-cm-image-streams.yml -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:55.914397", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "imagestream.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" created", 
    "stdout_lines": [
        "imagestream.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" created"
    ]
}

## rhpam_bc_cm_showcase : Configure Business Central ImageStream
TASK [rhpam_bc_cm_showcase : Configure Business Central ImageStream] ***********
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166276.82-269059606820699 `" && echo ansible-tmp-1615166276.82-269059606820699="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166276.82-269059606820699 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp6g07Hv TO /opt/apb/.ansible/tmp/ansible-tmp-1615166276.82-269059606820699/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166276.82-269059606820699/ /opt/apb/.ansible/tmp/ansible-tmp-1615166276.82-269059606820699/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166276.82-269059606820699/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166276.82-269059606820699/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-businesscentral-rhel8-cm-showcase:7.9.0\"}]' -n rhpam-user1", 
    "delta": "0:00:00.757923", 
    "end": "2021-03-08 01:17:57.862750", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-businesscentral-rhel8-cm-showcase:7.9.0\"}]' -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:57.104827", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched"
    ]
}

## rhpam_bc_cm_showcase : Configure Business Central ImageStream Namespace
TASK [rhpam_bc_cm_showcase : Configure Business Central ImageStream Namespace] ***
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166277.94-253274116990909 `" && echo ansible-tmp-1615166277.94-253274116990909="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166277.94-253274116990909 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmprPsknD TO /opt/apb/.ansible/tmp/ansible-tmp-1615166277.94-253274116990909/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166277.94-253274116990909/ /opt/apb/.ansible/tmp/ansible-tmp-1615166277.94-253274116990909/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166277.94-253274116990909/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166277.94-253274116990909/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user1\"}]' -n rhpam-user1", 
    "delta": "0:00:00.806046", 
    "end": "2021-03-08 01:17:59.043145", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user1\"}]' -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:58.237099", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched"
    ]
}

## rhpam_bc_cm_showcase : Configure Business Central environment variables.
TASK [rhpam_bc_cm_showcase : Configure Business Central environment variables.] ***
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:21
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166279.12-220012500182106 `" && echo ansible-tmp-1615166279.12-220012500182106="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166279.12-220012500182106 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp_Ag2Cc TO /opt/apb/.ansible/tmp/ansible-tmp-1615166279.12-220012500182106/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166279.12-220012500182106/ /opt/apb/.ansible/tmp/ansible-tmp-1615166279.12-220012500182106/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166279.12-220012500182106/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166279.12-220012500182106/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr JAVA_OPTS_APPEND=\"-Dorg.jbpm.casemgmt.showcase.url=/rhpam-case-mgmt-showcase -Dorg.kie.server.location=http://rhpam7-kieserver:8080/services/rest/server -Dorg.jbpm.wb.forms.renderer.ext=true\" -n rhpam-user1", 
    "delta": "0:00:00.873007", 
    "end": "2021-03-08 01:18:00.221006", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr JAVA_OPTS_APPEND=\"-Dorg.jbpm.casemgmt.showcase.url=/rhpam-case-mgmt-showcase -Dorg.kie.server.location=http://rhpam7-kieserver:8080/services/rest/server -Dorg.jbpm.wb.forms.renderer.ext=true\" -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:17:59.347999", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## 繰り返し (USER2)
TASK [rhpam_bc_cm_showcase : Check if ImageStream exists] **********************
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166280.31-30104315726658 `" && echo ansible-tmp-1615166280.31-30104315726658="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166280.31-30104315726658 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpZGjt7D TO /opt/apb/.ansible/tmp/ansible-tmp-1615166280.31-30104315726658/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166280.31-30104315726658/ /opt/apb/.ansible/tmp/ansible-tmp-1615166280.31-30104315726658/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166280.31-30104315726658/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166280.31-30104315726658/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get is/rhpam-businesscentral-rhel8-cm-showcase -n rhpam-user2", 
    "delta": "0:00:00.792070", 
    "end": "2021-03-08 01:18:01.334324", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is/rhpam-businesscentral-rhel8-cm-showcase -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:00.542254", 
    "stderr": "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [rhpam_bc_cm_showcase : Create ImageStream] *******************************
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166281.42-115511310299267 `" && echo ansible-tmp-1615166281.42-115511310299267="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166281.42-115511310299267 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpXDlhiV TO /opt/apb/.ansible/tmp/ansible-tmp-1615166281.42-115511310299267/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166281.42-115511310299267/ /opt/apb/.ansible/tmp/ansible-tmp-1615166281.42-115511310299267/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166281.42-115511310299267/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166281.42-115511310299267/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create -f /opt/ansible/roles/rhpam_bc_cm_showcase/files/rhpam79-bc-cm-image-streams.yml -n rhpam-user2", 
    "delta": "0:00:00.744294", 
    "end": "2021-03-08 01:18:02.446272", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create -f /opt/ansible/roles/rhpam_bc_cm_showcase/files/rhpam79-bc-cm-image-streams.yml -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:01.701978", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "imagestream.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" created", 
    "stdout_lines": [
        "imagestream.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" created"
    ]
}

TASK [rhpam_bc_cm_showcase : Configure Business Central ImageStream] ***********
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166282.51-176530090409719 `" && echo ansible-tmp-1615166282.51-176530090409719="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166282.51-176530090409719 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp9p8CYH TO /opt/apb/.ansible/tmp/ansible-tmp-1615166282.51-176530090409719/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166282.51-176530090409719/ /opt/apb/.ansible/tmp/ansible-tmp-1615166282.51-176530090409719/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166282.51-176530090409719/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166282.51-176530090409719/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-businesscentral-rhel8-cm-showcase:7.9.0\"}]' -n rhpam-user2", 
    "delta": "0:00:00.813894", 
    "end": "2021-03-08 01:18:03.550571", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-businesscentral-rhel8-cm-showcase:7.9.0\"}]' -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:02.736677", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched"
    ]
}

TASK [rhpam_bc_cm_showcase : Configure Business Central ImageStream Namespace] ***
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166283.62-266854931517166 `" && echo ansible-tmp-1615166283.62-266854931517166="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166283.62-266854931517166 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpy4lJ4S TO /opt/apb/.ansible/tmp/ansible-tmp-1615166283.62-266854931517166/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166283.62-266854931517166/ /opt/apb/.ansible/tmp/ansible-tmp-1615166283.62-266854931517166/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166283.62-266854931517166/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166283.62-266854931517166/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user2\"}]' -n rhpam-user2", 
    "delta": "0:00:00.838046", 
    "end": "2021-03-08 01:18:04.686690", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user2\"}]' -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:03.848644", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched"
    ]
}

TASK [rhpam_bc_cm_showcase : Configure Business Central environment variables.] ***
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:21
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166284.74-87403585434062 `" && echo ansible-tmp-1615166284.74-87403585434062="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166284.74-87403585434062 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpKyou08 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166284.74-87403585434062/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166284.74-87403585434062/ /opt/apb/.ansible/tmp/ansible-tmp-1615166284.74-87403585434062/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166284.74-87403585434062/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166284.74-87403585434062/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr JAVA_OPTS_APPEND=\"-Dorg.jbpm.casemgmt.showcase.url=/rhpam-case-mgmt-showcase -Dorg.kie.server.location=http://rhpam7-kieserver:8080/services/rest/server -Dorg.jbpm.wb.forms.renderer.ext=true\" -n rhpam-user2", 
    "delta": "0:00:00.833481", 
    "end": "2021-03-08 01:18:05.853155", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr JAVA_OPTS_APPEND=\"-Dorg.jbpm.casemgmt.showcase.url=/rhpam-case-mgmt-showcase -Dorg.kie.server.location=http://rhpam7-kieserver:8080/services/rest/server -Dorg.jbpm.wb.forms.renderer.ext=true\" -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:05.019674", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

## 繰り返し (USER3)
TASK [rhpam_bc_cm_showcase : Check if ImageStream exists] **********************
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166285.92-102664066471720 `" && echo ansible-tmp-1615166285.92-102664066471720="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166285.92-102664066471720 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpMBy7Un TO /opt/apb/.ansible/tmp/ansible-tmp-1615166285.92-102664066471720/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166285.92-102664066471720/ /opt/apb/.ansible/tmp/ansible-tmp-1615166285.92-102664066471720/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166285.92-102664066471720/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166285.92-102664066471720/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get is/rhpam-businesscentral-rhel8-cm-showcase -n rhpam-user3", 
    "delta": "0:00:00.739732", 
    "end": "2021-03-08 01:18:06.955083", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is/rhpam-businesscentral-rhel8-cm-showcase -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:06.215351", 
    "stderr": "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [rhpam_bc_cm_showcase : Create ImageStream] *******************************
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166287.1-238450543844129 `" && echo ansible-tmp-1615166287.1-238450543844129="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166287.1-238450543844129 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpdCX9fC TO /opt/apb/.ansible/tmp/ansible-tmp-1615166287.1-238450543844129/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166287.1-238450543844129/ /opt/apb/.ansible/tmp/ansible-tmp-1615166287.1-238450543844129/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166287.1-238450543844129/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166287.1-238450543844129/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create -f /opt/ansible/roles/rhpam_bc_cm_showcase/files/rhpam79-bc-cm-image-streams.yml -n rhpam-user3", 
    "delta": "0:00:00.896893", 
    "end": "2021-03-08 01:18:08.232783", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create -f /opt/ansible/roles/rhpam_bc_cm_showcase/files/rhpam79-bc-cm-image-streams.yml -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:07.335890", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "imagestream.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" created", 
    "stdout_lines": [
        "imagestream.image.openshift.io \"rhpam-businesscentral-rhel8-cm-showcase\" created"
    ]
}

TASK [rhpam_bc_cm_showcase : Configure Business Central ImageStream] ***********
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166288.31-204769124579745 `" && echo ansible-tmp-1615166288.31-204769124579745="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166288.31-204769124579745 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpvfxNZ5 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166288.31-204769124579745/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166288.31-204769124579745/ /opt/apb/.ansible/tmp/ansible-tmp-1615166288.31-204769124579745/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166288.31-204769124579745/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166288.31-204769124579745/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-businesscentral-rhel8-cm-showcase:7.9.0\"}]' -n rhpam-user3", 
    "delta": "0:00:00.776142", 
    "end": "2021-03-08 01:18:09.318664", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-businesscentral-rhel8-cm-showcase:7.9.0\"}]' -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:08.542522", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched"
    ]
}

TASK [rhpam_bc_cm_showcase : Configure Business Central ImageStream Namespace] ***
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166289.41-19448154411125 `" && echo ansible-tmp-1615166289.41-19448154411125="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166289.41-19448154411125 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpiSsao1 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166289.41-19448154411125/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166289.41-19448154411125/ /opt/apb/.ansible/tmp/ansible-tmp-1615166289.41-19448154411125/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166289.41-19448154411125/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166289.41-19448154411125/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user3\"}]' -n rhpam-user3", 
    "delta": "0:00:00.784671", 
    "end": "2021-03-08 01:18:10.486126", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-rhpamcentr --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user3\"}]' -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:09.701455", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-rhpamcentr\" patched"
    ]
}

TASK [rhpam_bc_cm_showcase : Configure Business Central environment variables.] ***
task path: /opt/ansible/roles/rhpam_bc_cm_showcase/tasks/main.yml:21
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166290.55-104794572520764 `" && echo ansible-tmp-1615166290.55-104794572520764="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166290.55-104794572520764 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpERLuQx TO /opt/apb/.ansible/tmp/ansible-tmp-1615166290.55-104794572520764/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166290.55-104794572520764/ /opt/apb/.ansible/tmp/ansible-tmp-1615166290.55-104794572520764/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166290.55-104794572520764/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166290.55-104794572520764/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-rhpamcentr JAVA_OPTS_APPEND=\"-Dorg.jbpm.casemgmt.showcase.url=/rhpam-case-mgmt-showcase -Dorg.kie.server.location=http://rhpam7-kieserver:8080/services/rest/server -Dorg.jbpm.wb.forms.renderer.ext=true\" -n rhpam-user3", 
    "delta": "0:00:00.810939", 
    "end": "2021-03-08 01:18:11.638713", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-rhpamcentr JAVA_OPTS_APPEND=\"-Dorg.jbpm.casemgmt.showcase.url=/rhpam-case-mgmt-showcase -Dorg.kie.server.location=http://rhpam7-kieserver:8080/services/rest/server -Dorg.jbpm.wb.forms.renderer.ext=true\" -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:10.827774", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-rhpamcentr\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-rhpamcentr\" updated"
    ]
}

# ここまで rhpam_bc_cm_showcase

# rhpam_ks_cors
TASK [include_role] ************************************************************
task path: /opt/apb/actions/provision.yml:268

## rhpam_ks_cors : Check if ImageStream exists
TASK [rhpam_ks_cors : Check if ImageStream exists] *****************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166292.24-61712250500213 `" && echo ansible-tmp-1615166292.24-61712250500213="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166292.24-61712250500213 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmplTD2Uo TO /opt/apb/.ansible/tmp/ansible-tmp-1615166292.24-61712250500213/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166292.24-61712250500213/ /opt/apb/.ansible/tmp/ansible-tmp-1615166292.24-61712250500213/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166292.24-61712250500213/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166292.24-61712250500213/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get is/rhpam-kieserver-rhel8-cors -n rhpam-user1", 
    "delta": "0:00:00.742456", 
    "end": "2021-03-08 01:18:13.260515", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is/rhpam-kieserver-rhel8-cors -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:12.518059", 
    "stderr": "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-kieserver-rhel8-cors\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-kieserver-rhel8-cors\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## rhpam_ks_cors : Create ImageStream
TASK [rhpam_ks_cors : Create ImageStream] **************************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166293.4-77844534251444 `" && echo ansible-tmp-1615166293.4-77844534251444="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166293.4-77844534251444 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpLTObYx TO /opt/apb/.ansible/tmp/ansible-tmp-1615166293.4-77844534251444/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166293.4-77844534251444/ /opt/apb/.ansible/tmp/ansible-tmp-1615166293.4-77844534251444/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166293.4-77844534251444/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166293.4-77844534251444/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create -f /opt/ansible/roles/rhpam_ks_cors/files/rhpam79-ks-cors-image-streams.yml -n rhpam-user1", 
    "delta": "0:00:00.801746", 
    "end": "2021-03-08 01:18:14.443050", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create -f /opt/ansible/roles/rhpam_ks_cors/files/rhpam79-ks-cors-image-streams.yml -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:13.641304", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "imagestream.image.openshift.io \"rhpam-kieserver-rhel8-cors\" created", 
    "stdout_lines": [
        "imagestream.image.openshift.io \"rhpam-kieserver-rhel8-cors\" created"
    ]
}

## rhpam_ks_cors : Configure KIE-Server ImageStream
TASK [rhpam_ks_cors : Configure KIE-Server ImageStream] ************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166294.52-136196456532731 `" && echo ansible-tmp-1615166294.52-136196456532731="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166294.52-136196456532731 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpatD1UR TO /opt/apb/.ansible/tmp/ansible-tmp-1615166294.52-136196456532731/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166294.52-136196456532731/ /opt/apb/.ansible/tmp/ansible-tmp-1615166294.52-136196456532731/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166294.52-136196456532731/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166294.52-136196456532731/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-kieserver-rhel8-cors:7.9.0\"}]' -n rhpam-user1", 
    "delta": "0:00:00.825298", 
    "end": "2021-03-08 01:18:15.629572", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-kieserver-rhel8-cors:7.9.0\"}]' -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:14.804274", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched"
    ]
}

## rhpam_ks_cors : Configure KIE-Server ImageStream Namespace
TASK [rhpam_ks_cors : Configure KIE-Server ImageStream Namespace] **************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166295.73-163907657120341 `" && echo ansible-tmp-1615166295.73-163907657120341="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166295.73-163907657120341 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmppG922b TO /opt/apb/.ansible/tmp/ansible-tmp-1615166295.73-163907657120341/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166295.73-163907657120341/ /opt/apb/.ansible/tmp/ansible-tmp-1615166295.73-163907657120341/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166295.73-163907657120341/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166295.73-163907657120341/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user1\"}]' -n rhpam-user1", 
    "delta": "0:00:00.758477", 
    "end": "2021-03-08 01:18:16.772781", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user1\"}]' -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:16.014304", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched"
    ]
}

## rhpam_ks_cors : Configure KIE-Server Property for REST Calls
TASK [rhpam_ks_cors : Configure KIE-Server Property for REST Calls] ************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:21
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166296.84-208306236651617 `" && echo ansible-tmp-1615166296.84-208306236651617="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166296.84-208306236651617 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmprmJnLa TO /opt/apb/.ansible/tmp/ansible-tmp-1615166296.84-208306236651617/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166296.84-208306236651617/ /opt/apb/.ansible/tmp/ansible-tmp-1615166296.84-208306236651617/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166296.84-208306236651617/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166296.84-208306236651617/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-kieserver DROOLS_SERVER_FILTER_CLASSES=false -n rhpam-user1", 
    "delta": "0:00:00.842108", 
    "end": "2021-03-08 01:18:17.971720", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-kieserver DROOLS_SERVER_FILTER_CLASSES=false -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:17.129612", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-kieserver\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-kieserver\" updated"
    ]
}

## 繰り返し (USER2)
TASK [rhpam_ks_cors : Check if ImageStream exists] *****************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166298.04-200328215617669 `" && echo ansible-tmp-1615166298.04-200328215617669="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166298.04-200328215617669 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpYiBStL TO /opt/apb/.ansible/tmp/ansible-tmp-1615166298.04-200328215617669/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166298.04-200328215617669/ /opt/apb/.ansible/tmp/ansible-tmp-1615166298.04-200328215617669/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166298.04-200328215617669/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166298.04-200328215617669/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get is/rhpam-kieserver-rhel8-cors -n rhpam-user2", 
    "delta": "0:00:00.734349", 
    "end": "2021-03-08 01:18:19.054880", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is/rhpam-kieserver-rhel8-cors -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:18.320531", 
    "stderr": "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-kieserver-rhel8-cors\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-kieserver-rhel8-cors\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [rhpam_ks_cors : Create ImageStream] **************************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166299.15-91987008444993 `" && echo ansible-tmp-1615166299.15-91987008444993="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166299.15-91987008444993 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp8xBfjb TO /opt/apb/.ansible/tmp/ansible-tmp-1615166299.15-91987008444993/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166299.15-91987008444993/ /opt/apb/.ansible/tmp/ansible-tmp-1615166299.15-91987008444993/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166299.15-91987008444993/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166299.15-91987008444993/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create -f /opt/ansible/roles/rhpam_ks_cors/files/rhpam79-ks-cors-image-streams.yml -n rhpam-user2", 
    "delta": "0:00:00.805624", 
    "end": "2021-03-08 01:18:20.243970", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create -f /opt/ansible/roles/rhpam_ks_cors/files/rhpam79-ks-cors-image-streams.yml -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:19.438346", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "imagestream.image.openshift.io \"rhpam-kieserver-rhel8-cors\" created", 
    "stdout_lines": [
        "imagestream.image.openshift.io \"rhpam-kieserver-rhel8-cors\" created"
    ]
}

TASK [rhpam_ks_cors : Configure KIE-Server ImageStream] ************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166300.53-6847803649302 `" && echo ansible-tmp-1615166300.53-6847803649302="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166300.53-6847803649302 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp66N_ze TO /opt/apb/.ansible/tmp/ansible-tmp-1615166300.53-6847803649302/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166300.53-6847803649302/ /opt/apb/.ansible/tmp/ansible-tmp-1615166300.53-6847803649302/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166300.53-6847803649302/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166300.53-6847803649302/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-kieserver-rhel8-cors:7.9.0\"}]' -n rhpam-user2", 
    "delta": "0:00:00.789125", 
    "end": "2021-03-08 01:18:21.605368", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-kieserver-rhel8-cors:7.9.0\"}]' -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:20.816243", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched"
    ]
}

TASK [rhpam_ks_cors : Configure KIE-Server ImageStream Namespace] **************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166301.72-167251439262087 `" && echo ansible-tmp-1615166301.72-167251439262087="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166301.72-167251439262087 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpPo_iDy TO /opt/apb/.ansible/tmp/ansible-tmp-1615166301.72-167251439262087/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166301.72-167251439262087/ /opt/apb/.ansible/tmp/ansible-tmp-1615166301.72-167251439262087/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166301.72-167251439262087/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166301.72-167251439262087/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user2\"}]' -n rhpam-user2", 
    "delta": "0:00:00.759936", 
    "end": "2021-03-08 01:18:22.767291", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user2\"}]' -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:22.007355", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched"
    ]
}

TASK [rhpam_ks_cors : Configure KIE-Server Property for REST Calls] ************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:21
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166302.84-235382975747854 `" && echo ansible-tmp-1615166302.84-235382975747854="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166302.84-235382975747854 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpTOR8hk TO /opt/apb/.ansible/tmp/ansible-tmp-1615166302.84-235382975747854/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166302.84-235382975747854/ /opt/apb/.ansible/tmp/ansible-tmp-1615166302.84-235382975747854/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166302.84-235382975747854/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166302.84-235382975747854/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-kieserver DROOLS_SERVER_FILTER_CLASSES=false -n rhpam-user2", 
    "delta": "0:00:00.822334", 
    "end": "2021-03-08 01:18:23.947010", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-kieserver DROOLS_SERVER_FILTER_CLASSES=false -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:23.124676", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-kieserver\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-kieserver\" updated"
    ]
}

## 繰り返し (USER3)
TASK [rhpam_ks_cors : Check if ImageStream exists] *****************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:3
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166304.02-7584048846212 `" && echo ansible-tmp-1615166304.02-7584048846212="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166304.02-7584048846212 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpxMBvUa TO /opt/apb/.ansible/tmp/ansible-tmp-1615166304.02-7584048846212/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166304.02-7584048846212/ /opt/apb/.ansible/tmp/ansible-tmp-1615166304.02-7584048846212/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166304.02-7584048846212/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166304.02-7584048846212/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get is/rhpam-kieserver-rhel8-cors -n rhpam-user3", 
    "delta": "0:00:00.744064", 
    "end": "2021-03-08 01:18:25.050329", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get is/rhpam-kieserver-rhel8-cors -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:24.306265", 
    "stderr": "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-kieserver-rhel8-cors\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): imagestreams.image.openshift.io \"rhpam-kieserver-rhel8-cors\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [rhpam_ks_cors : Create ImageStream] **************************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:9
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166305.14-154517127741650 `" && echo ansible-tmp-1615166305.14-154517127741650="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166305.14-154517127741650 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpW2FWux TO /opt/apb/.ansible/tmp/ansible-tmp-1615166305.14-154517127741650/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166305.14-154517127741650/ /opt/apb/.ansible/tmp/ansible-tmp-1615166305.14-154517127741650/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166305.14-154517127741650/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166305.14-154517127741650/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc create -f /opt/ansible/roles/rhpam_ks_cors/files/rhpam79-ks-cors-image-streams.yml -n rhpam-user3", 
    "delta": "0:00:00.840534", 
    "end": "2021-03-08 01:18:26.264028", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc create -f /opt/ansible/roles/rhpam_ks_cors/files/rhpam79-ks-cors-image-streams.yml -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:25.423494", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "imagestream.image.openshift.io \"rhpam-kieserver-rhel8-cors\" created", 
    "stdout_lines": [
        "imagestream.image.openshift.io \"rhpam-kieserver-rhel8-cors\" created"
    ]
}

TASK [rhpam_ks_cors : Configure KIE-Server ImageStream] ************************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:13
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166306.34-120616337609743 `" && echo ansible-tmp-1615166306.34-120616337609743="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166306.34-120616337609743 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpsHJxyR TO /opt/apb/.ansible/tmp/ansible-tmp-1615166306.34-120616337609743/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166306.34-120616337609743/ /opt/apb/.ansible/tmp/ansible-tmp-1615166306.34-120616337609743/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166306.34-120616337609743/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166306.34-120616337609743/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-kieserver-rhel8-cors:7.9.0\"}]' -n rhpam-user3", 
    "delta": "0:00:00.859962", 
    "end": "2021-03-08 01:18:27.504720", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/name\", \"value\": \"rhpam-kieserver-rhel8-cors:7.9.0\"}]' -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:26.644758", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched"
    ]
}

TASK [rhpam_ks_cors : Configure KIE-Server ImageStream Namespace] **************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:17
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166307.61-130551373465955 `" && echo ansible-tmp-1615166307.61-130551373465955="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166307.61-130551373465955 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpJwR2SP TO /opt/apb/.ansible/tmp/ansible-tmp-1615166307.61-130551373465955/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166307.61-130551373465955/ /opt/apb/.ansible/tmp/ansible-tmp-1615166307.61-130551373465955/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166307.61-130551373465955/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166307.61-130551373465955/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user3\"}]' -n rhpam-user3", 
    "delta": "0:00:00.836543", 
    "end": "2021-03-08 01:18:28.759297", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc patch dc/rhpam7-kieserver --type='json' -p '[{\"op\": \"replace\", \"path\": \"/spec/triggers/0/imageChangeParams/from/namespace\", \"value\": \"rhpam-user3\"}]' -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:27.922754", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched", 
    "stdout_lines": [
        "deploymentconfig.apps.openshift.io \"rhpam7-kieserver\" patched"
    ]
}

TASK [rhpam_ks_cors : Configure KIE-Server Property for REST Calls] ************
task path: /opt/ansible/roles/rhpam_ks_cors/tasks/main.yml:21
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166308.83-51169365118327 `" && echo ansible-tmp-1615166308.83-51169365118327="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166308.83-51169365118327 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpQoPFFl TO /opt/apb/.ansible/tmp/ansible-tmp-1615166308.83-51169365118327/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166308.83-51169365118327/ /opt/apb/.ansible/tmp/ansible-tmp-1615166308.83-51169365118327/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166308.83-51169365118327/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166308.83-51169365118327/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc set env dc/rhpam7-kieserver DROOLS_SERVER_FILTER_CLASSES=false -n rhpam-user3", 
    "delta": "0:00:00.854783", 
    "end": "2021-03-08 01:18:29.970664", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc set env dc/rhpam7-kieserver DROOLS_SERVER_FILTER_CLASSES=false -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:29.115881", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "deploymentconfig \"rhpam7-kieserver\" updated", 
    "stdout_lines": [
        "deploymentconfig \"rhpam7-kieserver\" updated"
    ]
}

# ここまで rhpam_ks_cors

# ./rhpam_decision-test-app.yml
TASK [include_tasks] ***********************************************************
task path: /opt/apb/actions/provision.yml:274
included: /opt/apb/actions/rhpam_decision-test-app.yml for localhost
included: /opt/apb/actions/rhpam_decision-test-app.yml for localhost
included: /opt/apb/actions/rhpam_decision-test-app.yml for localhost

## rhpam_decision-test-app.yml : Check if ReactJS Decision Client App exists
TASK [Check if ReactJS Decision Client App exists] *****************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:2
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166310.32-75414406959204 `" && echo ansible-tmp-1615166310.32-75414406959204="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166310.32-75414406959204 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpUHzfim TO /opt/apb/.ansible/tmp/ansible-tmp-1615166310.32-75414406959204/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166310.32-75414406959204/ /opt/apb/.ansible/tmp/ansible-tmp-1615166310.32-75414406959204/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166310.32-75414406959204/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166310.32-75414406959204/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get dc/react-web-app -n rhpam-user1", 
    "delta": "0:00:00.793375", 
    "end": "2021-03-08 01:18:31.403214", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get dc/react-web-app -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:30.609839", 
    "stderr": "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"react-web-app\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"react-web-app\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

## rhpam_decision-test-app.yml : Get KIE Server Route
TASK [Get KIE Server Route] ****************************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:8
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166311.51-234001533167432 `" && echo ansible-tmp-1615166311.51-234001533167432="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166311.51-234001533167432 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmptrAIQQ TO /opt/apb/.ansible/tmp/ansible-tmp-1615166311.51-234001533167432/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166311.51-234001533167432/ /opt/apb/.ansible/tmp/ansible-tmp-1615166311.51-234001533167432/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166311.51-234001533167432/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166311.51-234001533167432/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get route insecure-rhpam7-kieserver -n rhpam-user1 | awk 'FNR > 1 {print $2}'", 
    "delta": "0:00:00.885198", 
    "end": "2021-03-08 01:18:32.631397", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get route insecure-rhpam7-kieserver -n rhpam-user1 | awk 'FNR > 1 {print $2}'", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:31.746199", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "insecure-rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com", 
    "stdout_lines": [
        "insecure-rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com"
    ]
}

## rhpam_decision-test-app.yml : Set KIE-Server Route fact
TASK [Set KIE-Server Route fact] ***********************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:13
ok: [localhost] => {
    "ansible_facts": {
        "kie_server_route": "insecure-rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "changed": false
}

## rhpam_decision-test-app.yml : Create ReactJS Decision Client App
TASK [Create ReactJS Decision Client App] **************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:18
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166312.81-277283650481519 `" && echo ansible-tmp-1615166312.81-277283650481519="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166312.81-277283650481519 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpU4Sgu6 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166312.81-277283650481519/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166312.81-277283650481519/ /opt/apb/.ansible/tmp/ansible-tmp-1615166312.81-277283650481519/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166312.81-277283650481519/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166312.81-277283650481519/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app -e KIE_SERVER_URL=http://insecure-rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com -e KIE_SERVER_USER=pamAdmin -e KIE_SERVER_PWD=redhatpam1! --template react-web-app -p SOURCE_REPOSITORY_URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client -n rhpam-user1", 
    "delta": "0:00:01.376612", 
    "end": "2021-03-08 01:18:34.417176", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app -e KIE_SERVER_URL=http://insecure-rhpam7-kieserver-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com -e KIE_SERVER_USER=pamAdmin -e KIE_SERVER_PWD=redhatpam1! --template react-web-app -p SOURCE_REPOSITORY_URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client -n rhpam-user1", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:33.040564", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Deploying template \"openshift/react-web-app\" to project rhpam-user1\n\n     react-web-app\n     ---------\n     Just building a little react app with a web builder\n\n     * With parameters:\n        * Application name=react-web-app\n        * Source URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client\n        * Source Branch=master\n        * Source Directory=.\n        * Output Directory=build\n        * GitHub Webhook Secret=QYktaXiCiXTLyBgMqmstHR5L3XcKlTJEACpC1cLq # generated\n\n--> Creating resources ...\n    imagestream \"react-web-app-builder\" created\n    imagestream \"react-web-app-runtime\" created\n    imagestream \"web-app-builder-runtime\" created\n    imagestream \"nginx-image-runtime\" created\n    buildconfig \"react-web-app-builder\" created\n    buildconfig \"react-web-app-runtime\" created\n    deploymentconfig \"react-web-app\" created\n    service \"react-web-app\" created\n    route \"react-web-app\" created\n--> Success\n    Build scheduled, use 'oc logs -f bc/react-web-app-builder' to track its progress.\n    Build scheduled, use 'oc logs -f bc/react-web-app-runtime' to track its progress.\n    Access your application via route 'react-web-app-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Run 'oc status' to view your app.", 
    "stdout_lines": [
        "--> Deploying template \"openshift/react-web-app\" to project rhpam-user1", 
        "", 
        "     react-web-app", 
        "     ---------", 
        "     Just building a little react app with a web builder", 
        "", 
        "     * With parameters:", 
        "        * Application name=react-web-app", 
        "        * Source URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client", 
        "        * Source Branch=master", 
        "        * Source Directory=.", 
        "        * Output Directory=build", 
        "        * GitHub Webhook Secret=QYktaXiCiXTLyBgMqmstHR5L3XcKlTJEACpC1cLq # generated", 
        "", 
        "--> Creating resources ...", 
        "    imagestream \"react-web-app-builder\" created", 
        "    imagestream \"react-web-app-runtime\" created", 
        "    imagestream \"web-app-builder-runtime\" created", 
        "    imagestream \"nginx-image-runtime\" created", 
        "    buildconfig \"react-web-app-builder\" created", 
        "    buildconfig \"react-web-app-runtime\" created", 
        "    deploymentconfig \"react-web-app\" created", 
        "    service \"react-web-app\" created", 
        "    route \"react-web-app\" created", 
        "--> Success", 
        "    Build scheduled, use 'oc logs -f bc/react-web-app-builder' to track its progress.", 
        "    Build scheduled, use 'oc logs -f bc/react-web-app-runtime' to track its progress.", 
        "    Access your application via route 'react-web-app-rhpam-user1.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Run 'oc status' to view your app."
    ]
}

## 繰り返し (USER2)
TASK [Check if ReactJS Decision Client App exists] *****************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:2
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166314.52-116788169556883 `" && echo ansible-tmp-1615166314.52-116788169556883="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166314.52-116788169556883 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpnHzHUw TO /opt/apb/.ansible/tmp/ansible-tmp-1615166314.52-116788169556883/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166314.52-116788169556883/ /opt/apb/.ansible/tmp/ansible-tmp-1615166314.52-116788169556883/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166314.52-116788169556883/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166314.52-116788169556883/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get dc/react-web-app -n rhpam-user2", 
    "delta": "0:00:00.847266", 
    "end": "2021-03-08 01:18:35.662314", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get dc/react-web-app -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:34.815048", 
    "stderr": "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"react-web-app\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"react-web-app\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [Get KIE Server Route] ****************************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:8
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166315.8-39684569029840 `" && echo ansible-tmp-1615166315.8-39684569029840="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166315.8-39684569029840 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpKdabtR TO /opt/apb/.ansible/tmp/ansible-tmp-1615166315.8-39684569029840/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166315.8-39684569029840/ /opt/apb/.ansible/tmp/ansible-tmp-1615166315.8-39684569029840/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166315.8-39684569029840/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166315.8-39684569029840/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get route insecure-rhpam7-kieserver -n rhpam-user2 | awk 'FNR > 1 {print $2}'", 
    "delta": "0:00:00.861639", 
    "end": "2021-03-08 01:18:36.905601", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get route insecure-rhpam7-kieserver -n rhpam-user2 | awk 'FNR > 1 {print $2}'", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:36.043962", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "insecure-rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com", 
    "stdout_lines": [
        "insecure-rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com"
    ]
}

TASK [Set KIE-Server Route fact] ***********************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:13
ok: [localhost] => {
    "ansible_facts": {
        "kie_server_route": "insecure-rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "changed": false
}

TASK [Create ReactJS Decision Client App] **************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:18
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166317.05-72948941741728 `" && echo ansible-tmp-1615166317.05-72948941741728="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166317.05-72948941741728 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmp0MKb6U TO /opt/apb/.ansible/tmp/ansible-tmp-1615166317.05-72948941741728/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166317.05-72948941741728/ /opt/apb/.ansible/tmp/ansible-tmp-1615166317.05-72948941741728/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166317.05-72948941741728/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166317.05-72948941741728/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app -e KIE_SERVER_URL=http://insecure-rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com -e KIE_SERVER_USER=pamAdmin -e KIE_SERVER_PWD=redhatpam1! --template react-web-app -p SOURCE_REPOSITORY_URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client -n rhpam-user2", 
    "delta": "0:00:01.296404", 
    "end": "2021-03-08 01:18:38.634165", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app -e KIE_SERVER_URL=http://insecure-rhpam7-kieserver-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com -e KIE_SERVER_USER=pamAdmin -e KIE_SERVER_PWD=redhatpam1! --template react-web-app -p SOURCE_REPOSITORY_URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client -n rhpam-user2", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:37.337761", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Deploying template \"openshift/react-web-app\" to project rhpam-user2\n\n     react-web-app\n     ---------\n     Just building a little react app with a web builder\n\n     * With parameters:\n        * Application name=react-web-app\n        * Source URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client\n        * Source Branch=master\n        * Source Directory=.\n        * Output Directory=build\n        * GitHub Webhook Secret=gIlDm17mb1CTjhLqt6jRLmSbi1LXTFlSxccvdti5 # generated\n\n--> Creating resources ...\n    imagestream \"react-web-app-builder\" created\n    imagestream \"react-web-app-runtime\" created\n    imagestream \"web-app-builder-runtime\" created\n    imagestream \"nginx-image-runtime\" created\n    buildconfig \"react-web-app-builder\" created\n    buildconfig \"react-web-app-runtime\" created\n    deploymentconfig \"react-web-app\" created\n    service \"react-web-app\" created\n    route \"react-web-app\" created\n--> Success\n    Build scheduled, use 'oc logs -f bc/react-web-app-builder' to track its progress.\n    Build scheduled, use 'oc logs -f bc/react-web-app-runtime' to track its progress.\n    Access your application via route 'react-web-app-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Run 'oc status' to view your app.", 
    "stdout_lines": [
        "--> Deploying template \"openshift/react-web-app\" to project rhpam-user2", 
        "", 
        "     react-web-app", 
        "     ---------", 
        "     Just building a little react app with a web builder", 
        "", 
        "     * With parameters:", 
        "        * Application name=react-web-app", 
        "        * Source URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client", 
        "        * Source Branch=master", 
        "        * Source Directory=.", 
        "        * Output Directory=build", 
        "        * GitHub Webhook Secret=gIlDm17mb1CTjhLqt6jRLmSbi1LXTFlSxccvdti5 # generated", 
        "", 
        "--> Creating resources ...", 
        "    imagestream \"react-web-app-builder\" created", 
        "    imagestream \"react-web-app-runtime\" created", 
        "    imagestream \"web-app-builder-runtime\" created", 
        "    imagestream \"nginx-image-runtime\" created", 
        "    buildconfig \"react-web-app-builder\" created", 
        "    buildconfig \"react-web-app-runtime\" created", 
        "    deploymentconfig \"react-web-app\" created", 
        "    service \"react-web-app\" created", 
        "    route \"react-web-app\" created", 
        "--> Success", 
        "    Build scheduled, use 'oc logs -f bc/react-web-app-builder' to track its progress.", 
        "    Build scheduled, use 'oc logs -f bc/react-web-app-runtime' to track its progress.", 
        "    Access your application via route 'react-web-app-rhpam-user2.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Run 'oc status' to view your app."
    ]
}

## 繰り返し (USER3)
TASK [Check if ReactJS Decision Client App exists] *****************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:2
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166318.73-272626599105724 `" && echo ansible-tmp-1615166318.73-272626599105724="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166318.73-272626599105724 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpM9dkUv TO /opt/apb/.ansible/tmp/ansible-tmp-1615166318.73-272626599105724/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166318.73-272626599105724/ /opt/apb/.ansible/tmp/ansible-tmp-1615166318.73-272626599105724/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166318.73-272626599105724/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166318.73-272626599105724/ > /dev/null 2>&1 && sleep 0'
fatal: [localhost]: FAILED! => {
    "changed": false, 
    "cmd": "oc get dc/react-web-app -n rhpam-user3", 
    "delta": "0:00:00.802320", 
    "end": "2021-03-08 01:18:39.835292", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get dc/react-web-app -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "msg": "non-zero return code", 
    "rc": 1, 
    "start": "2021-03-08 01:18:39.032972", 
    "stderr": "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"react-web-app\" not found", 
    "stderr_lines": [
        "Error from server (NotFound): deploymentconfigs.apps.openshift.io \"react-web-app\" not found"
    ], 
    "stdout": "", 
    "stdout_lines": []
}
...ignoring

TASK [Get KIE Server Route] ****************************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:8
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166319.93-203468754892549 `" && echo ansible-tmp-1615166319.93-203468754892549="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166319.93-203468754892549 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpKdQ8t0 TO /opt/apb/.ansible/tmp/ansible-tmp-1615166319.93-203468754892549/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166319.93-203468754892549/ /opt/apb/.ansible/tmp/ansible-tmp-1615166319.93-203468754892549/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166319.93-203468754892549/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166319.93-203468754892549/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc get route insecure-rhpam7-kieserver -n rhpam-user3 | awk 'FNR > 1 {print $2}'", 
    "delta": "0:00:00.814308", 
    "end": "2021-03-08 01:18:41.031406", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc get route insecure-rhpam7-kieserver -n rhpam-user3 | awk 'FNR > 1 {print $2}'", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:40.217098", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "insecure-rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com", 
    "stdout_lines": [
        "insecure-rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com"
    ]
}

TASK [Set KIE-Server Route fact] ***********************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:13
ok: [localhost] => {
    "ansible_facts": {
        "kie_server_route": "insecure-rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com"
    }, 
    "changed": false
}

TASK [Create ReactJS Decision Client App] **************************************
task path: /opt/apb/actions/rhpam_decision-test-app.yml:18
Using module file /usr/lib/python2.7/site-packages/ansible/modules/commands/command.py
<localhost> ESTABLISH LOCAL CONNECTION FOR USER: apb
<localhost> EXEC /bin/sh -c 'echo ~apb && sleep 0'
<localhost> EXEC /bin/sh -c '( umask 77 && mkdir -p "` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166321.21-194755487018771 `" && echo ansible-tmp-1615166321.21-194755487018771="` echo /opt/apb/.ansible/tmp/ansible-tmp-1615166321.21-194755487018771 `" ) && sleep 0'
<localhost> PUT /opt/apb/.ansible/tmp/ansible-local-9MuxFLy/tmpkAXHYi TO /opt/apb/.ansible/tmp/ansible-tmp-1615166321.21-194755487018771/command.py
<localhost> EXEC /bin/sh -c 'chmod u+x /opt/apb/.ansible/tmp/ansible-tmp-1615166321.21-194755487018771/ /opt/apb/.ansible/tmp/ansible-tmp-1615166321.21-194755487018771/command.py && sleep 0'
<localhost> EXEC /bin/sh -c '/usr/bin/python /opt/apb/.ansible/tmp/ansible-tmp-1615166321.21-194755487018771/command.py && sleep 0'
<localhost> EXEC /bin/sh -c 'rm -f -r /opt/apb/.ansible/tmp/ansible-tmp-1615166321.21-194755487018771/ > /dev/null 2>&1 && sleep 0'
changed: [localhost] => {
    "changed": true, 
    "cmd": "oc new-app -e KIE_SERVER_URL=http://insecure-rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com -e KIE_SERVER_USER=pamAdmin -e KIE_SERVER_PWD=redhatpam1! --template react-web-app -p SOURCE_REPOSITORY_URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client -n rhpam-user3", 
    "delta": "0:00:01.357200", 
    "end": "2021-03-08 01:18:42.805307", 
    "invocation": {
        "module_args": {
            "_raw_params": "oc new-app -e KIE_SERVER_URL=http://insecure-rhpam7-kieserver-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com -e KIE_SERVER_USER=pamAdmin -e KIE_SERVER_PWD=redhatpam1! --template react-web-app -p SOURCE_REPOSITORY_URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client -n rhpam-user3", 
            "_uses_shell": true, 
            "chdir": null, 
            "creates": null, 
            "executable": null, 
            "removes": null, 
            "stdin": null, 
            "warn": true
        }
    }, 
    "rc": 0, 
    "start": "2021-03-08 01:18:41.448107", 
    "stderr": "", 
    "stderr_lines": [], 
    "stdout": "--> Deploying template \"openshift/react-web-app\" to project rhpam-user3\n\n     react-web-app\n     ---------\n     Just building a little react app with a web builder\n\n     * With parameters:\n        * Application name=react-web-app\n        * Source URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client\n        * Source Branch=master\n        * Source Directory=.\n        * Output Directory=build\n        * GitHub Webhook Secret=VR5T08DJ0CjkJDwgs0GI2JgHSfktjJ2v4KAgH2df # generated\n\n--> Creating resources ...\n    imagestream \"react-web-app-builder\" created\n    imagestream \"react-web-app-runtime\" created\n    imagestream \"web-app-builder-runtime\" created\n    imagestream \"nginx-image-runtime\" created\n    buildconfig \"react-web-app-builder\" created\n    buildconfig \"react-web-app-runtime\" created\n    deploymentconfig \"react-web-app\" created\n    service \"react-web-app\" created\n    route \"react-web-app\" created\n--> Success\n    Build scheduled, use 'oc logs -f bc/react-web-app-builder' to track its progress.\n    Build scheduled, use 'oc logs -f bc/react-web-app-runtime' to track its progress.\n    Access your application via route 'react-web-app-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' \n    Run 'oc status' to view your app.", 
    "stdout_lines": [
        "--> Deploying template \"openshift/react-web-app\" to project rhpam-user3", 
        "", 
        "     react-web-app", 
        "     ---------", 
        "     Just building a little react app with a web builder", 
        "", 
        "     * With parameters:", 
        "        * Application name=react-web-app", 
        "        * Source URL=https://github.com/jbossdemocentral/rhpam7-workshop-reactjs-rules-client", 
        "        * Source Branch=master", 
        "        * Source Directory=.", 
        "        * Output Directory=build", 
        "        * GitHub Webhook Secret=VR5T08DJ0CjkJDwgs0GI2JgHSfktjJ2v4KAgH2df # generated", 
        "", 
        "--> Creating resources ...", 
        "    imagestream \"react-web-app-builder\" created", 
        "    imagestream \"react-web-app-runtime\" created", 
        "    imagestream \"web-app-builder-runtime\" created", 
        "    imagestream \"nginx-image-runtime\" created", 
        "    buildconfig \"react-web-app-builder\" created", 
        "    buildconfig \"react-web-app-runtime\" created", 
        "    deploymentconfig \"react-web-app\" created", 
        "    service \"react-web-app\" created", 
        "    route \"react-web-app\" created", 
        "--> Success", 
        "    Build scheduled, use 'oc logs -f bc/react-web-app-builder' to track its progress.", 
        "    Build scheduled, use 'oc logs -f bc/react-web-app-runtime' to track its progress.", 
        "    Access your application via route 'react-web-app-rhpam-user3.apps.cluster-4b1a.4b1a.example.opentlc.com' ", 
        "    Run 'oc status' to view your app."
    ]
}
META: ran handlers
META: ran handlers

# ここまで rhpam_decision-test-app.yml

PLAY RECAP *********************************************************************
localhost                  : ok=163  changed=99   unreachable=0    failed=0   

kamori@kamori-mac ~ % 
