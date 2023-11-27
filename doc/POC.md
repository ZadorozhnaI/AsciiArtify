# Proof of Concept (PoC) по розгортанню GitOps-системи на k3d

Розгортаємо Kubernetes кластер за допомогою k3d

### Демо

![]()

### Інструкція з розгортання

Пояснення команд згідно демо

1. `k3d cluster create argo` 
 Створює Kubernetes кластер з назвою "argo"
2. `kubectl cluster-info`
 Виводить інформацію про стан та конфігурацію поточного кластера Kubernetes.
3. `kubectl get all -A`
 оказує всі ресурси (-A означає всі namespace) у кластері, включаючи поди, сервіси, розгортання тощо.
4. `kubectl create namespace argocd`
 Створює новий namespace (простір імен) з назвою "argocd".
5. `kubectl get ns`
 Показує всі namespace в кластері.
6. `kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`
 Встановлює ArgoCD у вказаному namespace, використовуючи конфігурацію, яка знаходиться за вказаним URL.
7. `kubectl get po -n argocd -w`
 Показує всі поди (процеси) у namespace "argocd" та оновлює вивід в режимі реального часу (з параметром -w).
8. `kubectl port-forward svc/argocd-server -n argocd 8080:443`
 Налаштовує перенаправлення портів для забезпечення доступу до ArgoCD через локальний порт 8080.
9. `kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`
 Виводить і декодує пароль для адміністратора ArgoCD, який використовується для входу в інтерфейс ArgoCD.

Ці команди допомагають створити Kubernetes кластер, встановити ArgoCD у вказаному namespace, налаштувати доступ до ArgoCD та отримати необхідну інформацію для подальшої роботи з ArgoCD.
