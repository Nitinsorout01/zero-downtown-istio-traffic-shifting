# Zero Downtime Istio Traffic Shifting 🚀

## 📌 Overview
This project shows how to achieve **Zero-Downtime Rolling Updates** in Kubernetes using **Istio traffic shifting**.  
The idea is to move traffic gradually from version **v1** of an app to version **v2**, without causing downtime for users.

---

## 🛠️ Tools Used
- Kubernetes
- Istio Service Mesh
- kubectl

---

## 🚀 Steps

### 1️⃣ Deploy Application Versions
```bash
kubectl apply -f deployment-v1.yaml
kubectl apply -f deployment-v2.yaml

##2️⃣ Define DestinationRule
This tells Istio about different versions of the app.
kubectl apply -f destination-rule.yaml

3️⃣ Apply VirtualService for Traffic Shifting
100% → v1
kubectl apply -f virtualservice-100-0.yaml

50% v1 / 50% v2
kubectl apply -f virtualservice-50-50.yaml

100% → v2
kubectl apply -f virtualservice-0-100.yaml

