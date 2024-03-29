# OpenShift PVC data migration.

YouTube video demo: https://youtu.be/zEchDqjbahA?si=1Z6fiFjDOIUHynSj

### Steps to migrate pvc data
1. download the migrate.sh script and add your service account.
2. create your service account \
   `oc create sa $SERVICE_ACCOUNT`
3. set the permissions for your service account \
   `oc adm policy add-scc-to-user anyuid system:serviceaccount:$NAMESPACE:$SERVICE_ACCOUNT`
4. create your new "target" pvc's
5. stop the source & destination pods
6. run the script \
   `sh migrate.sh $SOURCE_PVC $DESTINATION_PVC`
7. Update your deployment to point to the new pvc
8. Start your deployment/pod and verify the data

Check for job completion - `oc get jobs -o wide`


Credit to "https://justyn.io/til/migrate-kubernetes-pvc-to-another-pvc/"
