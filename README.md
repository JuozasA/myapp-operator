Example of Ansible Operator controlled Node.js app with MongoDB database
==

Example of Ansible Operator controlled Node.js app with MongoDB database and AMQ Broker operator (not connected to Node.js)

Deploy
=

* Make sure you are logged in as a User with cluster admin permissions

Deploy resources:
```
oc create -f deploy/crds/myapp.cloud-ninja.name_appdbs_crd.yaml
oc create -f deploy/crds/myapp.cloud-ninja.name_apps_crd.yaml
oc create -f deploy/service_account.yaml
oc create -f deploy/role.yaml
oc create -f deploy/role_binding.yaml
oc create -f deploy/operator.yaml
```

Once our operator is running and is listening for changes, let's create our App and AppDB Custom Resources:

```
oc create -f deploy/crds/myapp.cloud-ninja.name_v1alpha1_app_cr.yaml
oc create -f deploy/crds/myapp.cloud-ninja.name_v1alpha1_appdb_cr.yaml
```

Remove App and AppDB CRs
==
```
oc delete -f deploy/crds/myapp.cloud-ninja.name_v1alpha1_app_cr.yaml
oc delete -f deploy/crds/myapp.cloud-ninja.name_v1alpha1_appdb_cr.yaml
```
