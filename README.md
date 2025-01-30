# k8s installing cluster (Kubespray)
1. Installing Git & Ansible

apt install git ansible -y

2.Installing Python PIP

apt install python3-pip -y

3.Installing dependence

apt install python3-venv -y

4.Git clone Kubespray

git clone https://github.com/kubernetes-sigs/kubespray.git

5.Create and launch virtual enviriment (take actual comm.from Git Kubespray)

VENVDIR=kubespray-venv
KUBESPRAYDIR=kubespray
python3 -m venv $VENVDIR
source $VENVDIR/bin/activate
cd $KUBESPRAYDIR
pip install -U -r requirements.txt

6.Copy sample repository for inventory and host file

cp -rfp inventory/sample inventory/mycluster

7.Create inventory.ini file for Ansible & hosts.txt for K8s

8.Installing Cluster

ansible-playbook -i inventory/mycluster/$NAME_INVENTORY_FILE cluster.yml -b -v \
  --private-key=~/.ssh/$YOUR_PRIVATE_KEY
