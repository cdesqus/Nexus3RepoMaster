Deploy Nexus Registry

A. Buat Namespace
-> kubectl create namespace nexus

B. Apply PVC (Persistent Volume)
-> kubectl apply -f nexus-pvc.yaml

C.Deploy Nexus
-> kubectl apply -f nexus-deployment.yaml

D. Expose Service (NodePort)
-> kubectl apply -f nexus-service.yaml
--------------------------------------------------------
Akses Nexus Web UI
A. Cek port-nya:
-> kubectl get svc -n nexus

Akses Web:
http://<node-ip>:31234

Generate Password Admin:
kubectl exec -n nexus -it $(kubectl get pod -n nexus -l app=nexus -o jsonpath='{.items[0].metadata.name}') -- cat /nexus-data/admin.password
------------------------------------------------

🔧 4. Buat Repository di Web UI
Masuk ke Nexus UI → Repositories → Create Repository

Pilih docker (hosted)

Konfigurasi:

Name: docker-hosted

HTTP port: 5000

Deployment policy: Allow redeploy

Simpan
