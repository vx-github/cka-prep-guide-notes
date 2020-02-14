# Addendum to CKA/CKAD prep Workshop #1 (2020-02-13)

### Networking LAB - ping pod

```
# Create another Pod
k create deploy web2 --image=nginx

# Install jq and get pod IPs
apt-get install jq -y 
IP2=$(k get pods web-<TAB> -o json | jq -r '. | .status.podIP')
IP2=$(k get pods web2-<TAB> -o json | jq -r '. | .status.podIP')

# Add env variables for testing
k run dev --rm --image=busybox --env="IP1=${IP1}" --env="IP2=${IP2}" -it -- /bin/ash

# ping pods
ping $IP1
ping $IP2

```