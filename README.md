# Ansible Lab Environment

![N|Lab Environment](http://www.digitalinfo.nl/images/LabEnvironment.png)

The 'Control Node' is your own laptop/macbook/desktop that has the necessary software installed:

   - GIT
   - Vagrant
   - VirtualBox
   - Ansible

and by using a private network adapter with VirtualBox, you can access the nodes to be managed, in this case master, node1 and node2.

Through 'my network' you can reach your server with software tools and other content you might need. Internet access is also controlled by this server although your personal network might look a bit different, perhaps Internet is reachable directly on your local network.

With VirtualBox, your 'Control Node' will act as a bridge for your workers to have access to the Internet as well.

## Instructions:

Clone this repository with
```sh
git clone https://github.com/NicoOosterwijk/setup_ansible_lab.git
```

Then go into the directory and start vagrant with:
```sh
cd setup_ansible_lab
vagrant up
```

When the jobs are finished, you should have a Kubernetes control file named k8s-master in your .kube directory. Use this control file with:
```sh
export KUBECONFIG=~/.kube/k8s-master
```
With this you should be able to use **kubectl** on your local computer.

The following IP addresses are allocated:

Node      | IP address
--------- | -------------
master    | 172.25.250.20
node1     | 172.25.250.21
node2     | 172.25.250.22

# Have Fun!
