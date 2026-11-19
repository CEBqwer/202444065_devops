# 9주차

## kubectl get nodes
<pre>
  <code>
  % kubectl get nodes 
  NAME       STATUS   ROLES           AGE    VERSION
  minikube   Ready    control-plane   109m   v1.37.0
  </code>
</pre>

사용한 도구는 minikube. kind는 받지 않았다...

## deployment
<pre>
  <code>
  % kubectl create deployment guestbook --image=ghcr.io/cebqwer/guestbook:v1
    
  % kubectl delete pod -l app=guestbook
  
  % kubectl get pods -w
  NAME                        READY   STATUS              RESTARTS   AGE
  guestbook-9c954f445-b88md   1/1     Running             0          14m
  guestbook-9c954f445-b88md   1/1     Terminating         0          14m
  guestbook-9c954f445-b88md   1/1     Terminating         0          14m
  guestbook-9c954f445-jn4vk   0/1     Pending             0          0s
  guestbook-9c954f445-jn4vk   0/1     Pending             0          0s
  guestbook-9c954f445-jn4vk   0/1     ContainerCreating   0          0s
  guestbook-9c954f445-jn4vk   0/1     ContainerCreating   0          1s
  guestbook-9c954f445-jn4vk   1/1     Running             0          1s
  </code>
</pre>

deployment를 사용하면 원하는 상태를 자동으로 유지해준다. (자가치유)

## 브라우저에서 실행
<img width="1376" height="876" alt="image" src="https://github.com/user-attachments/assets/0f26216d-b116-4049-a1a2-f1dc2efa4241" />

## 명령형 vs 선언형
