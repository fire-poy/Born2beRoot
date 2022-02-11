# Born2beRoot
Born2beRoot project 42

EVAL

shasum debian11_64bit.vdi

head -n 2 /etc/os-release
/usr/sbin/aa-status
ss -tunlp
Attention, votre signature risque de changer à la suite de votre première évaluation. Pour pallier à ce problème, plusieurs solutions s’offrent à vous, comme dupliquer votre machine virtuelle ou encore utiliser les save state. 

- [x] Le mode TTY sera active pour des questions de sécurité
Interdit l'exécution de la commande sudo à partir d'autre chose qu'une console ou un terminal, notamment à partir de scripts cron ou cgi-bin. 

Rappel de l'utilisateur : chaque fois que vous avez besoin d'aide pour vérifier quelque chose, l'étudiant évalué devrait être en mesure de vous aider avec ses notes, etc 

- [x] CentOS et Debian. 
CentOS prive RedhatEntreprise Linux qui offre suport 
Difficile de mettre a jour major version 7.8 a 7.9 c’est bon
de 8 a 9 NON c’est mieux desinstaleer et reinstaller
bon pour systemes efemere

Debian
ubunto mint et autres sont bases sur denbian
Free software philosophy 
Offre des support par independantes
tres horizontal concecus democracy directe
Compatible pour upgrades renouvelles tout les deux ans.
user-friendly GUI graphic user interface
a vast amount of packages

- [x] Qu’est-ce que c’est
A Virtual Machine (VM) is a compute resource that uses software instead of a physical computer to run programs and deploy apps. Each virtual machine runs its own operating system and functions separately from the other VMs, even when they are all running on the same host. For example, you can run a virtual MacOS machine on a physical PC

- [x] Comment fonctionne une machine virtuelle. 
VM working through "Virtualization" technology. Virtualization uses software to simulate virtual hardware that allows VMs to run on a single host machin.
le Hypervisor demande a l’os pour avoir des ressources et il l’alouer c’est ressources a la virtual machine

- [x] Le but de machines virtuelles. 
VMs may be deployed to accommodate different levels of processing power needs, to run software that requires a different operating system, or to test applications in a safe, sandboxed environment.


- [x] Aptitude et apt
Apt low level package manager 
Aptitude high level package manager
While apt-get lacks UI, Aptitude has a text-only and interactive UI
Aptitude is vaster in functionality than apt-get and integrates functionalities of apt-get and its other variants including apt-mark and apt-cache.
In many situations involving installation, removal and conflict resolution for packages, Aptitude proves its worth rather than apt-get. Some of the situations include:
why et why-not

- [x] APPArmor
Security system that  provide tools to isolate applications from each other... and in turn isolate an attacker from the rest of the system when an application is compromised.

AppArmor ("Application Armor") is a Linux kernel security module that allows the system administrator to restrict programs' capabilities with per-program profiles. Profiles can allow capabilities like network access, raw socket access, and the permission to read, write, or execute files on matching paths.
Travail avec les chemin de fichier un fichier innacessible peut devenir accessible quand un lien est créé .

Is offered as an alternative to SELinux, which critics consider difficult for administrators to set up and maintain.
Travail avec le nom de fichier, un fichier innacessible peut devenir accessible lorsque les app mettent a jour le fichier


Uncomplicated Firewall (UFW) is a program for managing a netfilter firewall designed to be easy to use. 


ACTIONS
-Assurez-vous que la machine ne dispose pas d'un environnement graphique au lancement.

- Vérifiez que le service UFW est démarré avec l'aide de l'évaluateur. /usr/sbin/ufw status
- Vérifiez que le service SSH est démarré avec l'aide de l'évaluateur.
sudo systemctl status ssh  - Vérifiez que le système d'exploitation choisi est Debian ou CentOS avec l'aide de l'évaluateur. head -n 2 /etc/os-release
-un utilisateur avec le login de l'étudiant évalué soit présent
cut -d: -f1 /etc/passwd
-d delimiter :
-f1 field 1
awk -F “:” ‘{print $1}’ /etc/passwd
-Vérifiez qu'il a bien été ajouté et qu'il appartient aux groupes 'sudo' 
getent group sudo
-et 'user42'.
getent group user42
groups // tout le reste

-créez un nouvel utilisateur. 
sudo adduser new_username
-comment il a pu mettre en place les règles de mot de passe dans le sujet sur sa                                  -machine virtuelle? 
installer password quality checking library using command:
sudo apt-get install libpam-pwquality
provide some plug-in strength-checking for passwords
sudo vim /etc/pam.d/common-password
sudo vim /etc/login.defs

-demandez à l'étudiant évalué de créer un groupe nommé 'évaluant' 
sudo groupadd evaluant
-atribuez-le à cet utilisateur. 
sudo usermod -aG evaluant new_username
-vérifiez que cet utilisateur appartient au groupe 'évaluateur'. 
getent group evaluant
- expliquer les avantages de cette politique de mot de passe, ainsi que les avantages et les inconvénients de sa mise en œuvre. 

Hostname and partitions 
-Vérifiez que le nom d'hôte de la machine est correctement formaté comme -suit :login42  hostnamectl
-Modifiez ce nom d'hôte en remplacez le login par le vôtre, puis redémarrez  hostnamectl set-hostname new_hostname
sudo vim /etc/hosts // que hacemos??
sudo reboot
- Vous pouvez maintenant restaurer la machine sur le nom d'hôte d'origine. 

- Demandez à l'étudiant évalué comment afficher les partitions pour cette machine virtuelle. 
lsblk  
L'étudiant évalué doit vous expliquer brièvement le fonctionnement de LVM et de quoi il s'agit.
- Vérifiez que le programme 'sudo' est correctement installé sur la machine virtuelle. 
dpkg -l | grep sudo
- L'étudiant évalué devrait maintenant afficher l'affectation de votre nouvel utilisateur au ' sudo' group. 
sudo -v
usermod -aG sudo your_username
sudo visudo           (write)            ||     sudo vim /etc/sudoers (read)
sudo visudo te dis si tu afait des errreurs a l’heure d’enregistrer
L'étudiant évalué doit d'abord expliquer l'intérêt et le fonctionnement de sudo à l'aide d'exemples de son choix. 

Montrer la mise en œuvre des règles imposées par le sujet.
sudo visudo - Vérifier que le '/var/log/sudo/' existe et contient au moins un fichier. Vérifiez le contenu des fichiers dans ce dossier, vous devriez voir un historique des commandes utilisées avec sudo. Enfin, essayez d'exécuter une commande via sudo. Vérifiez si le ou les fichiers du dossier '/var/log/sudo/' ont été mis à jour. 

UFW 
- Vérifiez que le programme 'UFW' est correctement installé sur la machine virtuelle. dpkg -l | grep ufw
- Vérifiez qu'il fonctionne correctement. /usr/sbin/ufw status
- L'étudiant évalué doit expliquer à vous en gros ce qu'est UFW et la valeur de son utilisation. sudo grep Port /etc/ssh/sshd_config
- Énumérez les règles actives dans UFW. Une règle doit exister pour le port 4242. sudo ufw status numbered
- Ajoutez une nouvelle règle pour ouvrir le port 8080. 
sudo ufw allow 8080
Vérifiez que celle-ci a bien été ajoutée en listant les règles actives. - 
sudo ufw status numbered
Supprimez cette nouvelle règle
sudo ufw deny 8080
sudo ufw delete 
 SSH 
Vérifiez que le service SSH est correctement installé sur la machine virtuelle. dpkg -l || grep ssh
- Vérifiez qu'il fonctionne correctement.
sudo systemctl status ssh  Que est-ce c’est SSH et l'intérêt de l'utiliser.? 

- Vérifiez que le service SSH utilise uniquement le port 4242.
ssh mpons@127.0.0.1 -p 4242  L'étudiant évalué doit vous aider à utiliser SSH afin de vous 
connecter avec l'utilisateur nouvellement créé. ssh user@127.0.0.1 -p 4242

Script monitoring 

Comment fonctionne son script en vous montrant le code. s'exécute toutes les 10 minutes si bon fonctionnement du script vérifié
l'étudiant évalué doit s'assurer que ce script s'exécute toutes les minutes. 
sudo crontab -u root -e
Le script s'exécute correctement avec des valeurs dynamiques?
Yes/No 
Enfin, l'étudiant évalué doit arrêter l'exécution du script au démarrage du serveur, mais sans modifier le script lui-même. 
Au démarrage, il faudra vérifier que le script existe toujours au même endroit, que ses droits sont restés inchangés, et qu'il n'a pas été modifié. 

sudo usermod -aG evaluant new_username
a is for append 
