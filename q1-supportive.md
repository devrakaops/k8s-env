### To generate load
kubectl run load-generatorr --image=busybox -n autoscale -it -- /bin/sh
while true; do
  for i in 1 2 3 4 5 6 7 8 9 10; do
    wget -q -O- http://apache-server &
  done
  wait
done

### Now check the hpa and wait for 30 seconds
watch -n 1 kubectl get hpa -n autoscale

<img width="1090" height="99" alt="image" src="https://github.com/user-attachments/assets/1147d51f-95b8-497e-bdba-a757dbdc5bdd" />
<img width="1107" height="145" alt="image" src="https://github.com/user-attachments/assets/a29fa4af-a4e7-46c1-aa78-f81736643862" />
