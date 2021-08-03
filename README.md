#  Démarrage environnement Ansible et projet Git Ansible


ssh-copy-id -i  /home/stagiaire/.ssh/id_ed25519.pub stagiaire@ip_machine_projet

ansible -i inventory -m ping all
ansible -m ping --user stagiaire -b --ask-become-pass ubuntuProjet

# Creation du playbook pour initier la création du user ansible dans le server à distance

ansible-playbook bootstrap_playbook.yml --user stagiaire -b --ask-become-pass -e cible=machine_cible

# Lancement du playbook requirement pour l'installation du role ansible-role-docker__3.1.2
ansible-galaxy role install -f roles/requirements.yml -p roles

# Lancement du playbook deploy-docker
ansible-playbook deploy-docker.yml


