# DomainControler - Controlador de Domínio Samba 4
Instalação e Provisionamento do Samba 4

Configurando o Samba 4 como controlador de domínio do Active Directory.

Fiz a instalação e provisionamento usando a documentação oficial do Samba 4 em https://wiki.samba.org/index.php/Main_Page. É válido destacar que a documentação oficial traz algumas duplicidades de instalações de pacotes ou omissão de algumas configurações de determinadas distribuições. Um dos motivos dessa documentação é justamente servir de atalho tanto pra mim para próximas implantações quanto para a comunidade. 

Alguns pontos importantes a destacar acerca do SAMBA 4.
- O Samba 4 suporta apenas LDAP e Kerberos ( KDC ).
- Há Distinção entre instalação e provisionamento.
- A Instalação do Samba 4 varia em relação à distribuição Linux utilizada.
- O Samba 4 não dá suporte à renomeação da zona DNS do AD e do domínio Kerberos.
- O controlador de domínio do Samba se tornará resolvedor DNS para todas as máquinas ingressadas no domínio.

A instalação e provisionamento foi feita no Debian 11 como máquina virtual em um hypervisor KVM do Proxmox. O Debian foi instalado com as configurações padrão:
- Sistema de arquivos Ext4.
- Sem ambiente gráfico e setado apenas a instalação dos pacotes de sistema.
- Uma partição com o ponto de montagem / 

----CONFIGURAÇÃO DO DEBIAN 11----

#apt-get update
#apt-get upgrade

#nano /root/.bashrc

Descomentar as linhas:   

PS1='${debian_chroot:+($debian_chroot)}\h:\w\$ '
export LS_OPTIONS='--color=auto'
eval "$(dircolors)"
alias ls='ls $LS_OPTIONS'
alias ll='ls $LS_OPTIONS -l'
alias l='ls $LS_OPTIONS -lA'
#alias rm='rm -i'
#alias cp='cp -i'
#alias mv='mv -i'
                                                   
Obs: A edição do .bashrc é útil para melhorar a experiência do usuário com o shell bash, portanto, não é obrigatória para a instalação e provisionamento do Samba 4.

 
                       
