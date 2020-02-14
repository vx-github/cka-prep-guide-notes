# CKA/CKAD prep Workshop #1 (2020-02-13)

## Sources

### Cinq sources

- CKA Prep Guide Fork - https://gitlab.com/cinqict-devops/cka-prep-guide/
- CKA Pre by Thijs - https://github.com/FireDrunk/cinq-cka-prep
- k8s Vagrant LAB setup - https://github.com/viveleroy/k8s_lab

### External sources

- Exam cheatsheet - https://kubernetes.io/docs/reference/kubectl/cheatsheet/


## Contribution by Eric
- Presentation - https://gitlab.com/cinqict-devops/cka-prep-guide/-/tree/master/ppt

### Subjects
- Core concepts
- Networking
- Storage (not really covered yet)


### Networking LAB - ping pod
(https://gitlab.com/cinqict-devops/cka-prep-guide/-/blob/master/Networking/Lab_ping_pod.md)

```
# Create pod
k create deploy web --image=nginx
	
# View pod IP
k describe po web-...

# create second pod and ping
k run dev --rm --image=busybox -it -- /bin/ash
ping -c 5 POD_IP
 
# Cleanup
k delete deploy web
```

Some additional testing by Vincent: [addendum01_vincent_prep01.md]

### Networking LAB - Discovering Services
(https://gitlab.com/cinqict-devops/cka-prep-guide/-/blob/master/Networking/Lab_discovering_services.md)

```
# Create pod
k run web --image=nginx --port=80

# Show DNS env vars
k exec web-<TAB> env

# Create service
k expose deploy web --port=8080 --target-port=80

# Create pod and verify env vars and DNS
k run busybox --image=busybox -it /bin/ash
env
wget web:8080

# Create namespace
k create ns foo

# Create Pod and verify env vars and DNS
k --namespace=foo run busybox --image=busybox -it /bin/ash
env
wget web.default:8080
```

## Contribution by Thijs
### Scheduling
(https://github.com/FireDrunk/cinq-cka-prep/tree/master/scheduling)

~ todo

- Scheduling
- Observability
