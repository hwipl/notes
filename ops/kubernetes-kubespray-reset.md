# Reset Kubernetes Cluster with Kubespray

```console
$ cd $KUBESPRAY_REPO/kubespray
$ # note: change kubespray version
$ docker run --rm -it --mount type=bind,source="$(pwd)"/inventory/MyCluster,dst=/inventory --mount type=bind,source="${HOME}"/my-ssh-key,dst=/root/MyCluster/my-ssh-key quay.io/kubespray/kubespray:v2.20.0 bash
$ ansible-playbook -i /inventory/hosts.yaml --become --become-user=root reset.yml
$ # again just to make sure ;)
$ ansible-playbook -i /inventory/hosts.yaml --become --become-user=root reset.yml
```
