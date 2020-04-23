Example of Ansible Operator controlled Node.js app with MongoDB database
==

Example of Ansible Operator controlled Node.js app with MongoDB database. Example creates AMQ Broker operator with Artemis instances but they are not connected/integrated into Node.js app. It is purely to show how OLM operators can be integrated into Ansible Operator.

Prereqs
=
* oc binary (version depends on your OCP version)
* git (to clone the repository)

Deploy
=

* Make sure you are logged in as a User with `cluster-admin` permissions.

Deploy resources:
```
oc create -f deploy/crds/myapp.cloud-ninja.name_appdbs_crd.yaml
oc create -f deploy/crds/myapp.cloud-ninja.name_apps_crd.yaml
oc create -f deploy/service_account.yaml
oc create -f deploy/role.yaml
oc create -f deploy/role_binding.yaml
oc create -f deploy/operator.yaml
```

* Once our operator is running and is listening for changes, let's create our App and AppDB Custom Resources:

* Open `/deploy/crds/myapp.example.com_v1alpha1_app_cr.yaml` and change `weburl` parameter to your prefered route hostname.
* Open `/deploy/crds/myapp.example.com_v1alpha1_appdb_cr.yaml` and change `storage_class_name` parameter to your prefered StorageClass for dynamic PV provisioning for MongoDB StatefulSet.

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
