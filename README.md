# Script-Huawei

########## CONFIGURAR TÚNEL GRE NO SWITCH E ROTEADOR HUAWEI ##########

######## Explicação de cada campo ########

[~SwitchA] Número do túnel (0-255)

[*SwitchA-Tunnel1] protocolo do túnel

[*SwitchA-Tunnel1] configuração de ip da interface do túnel

[*SwitchA-Tunnel1] ip do equipamento que foi configurado o túnel

[*SwitchA-Tunnel1] ip do equipamento remoto 

[*SwitchA-Tunnel1] sair do modo de configuração


######## Configuração dos campos acima explicados ########

PONTA A

[~SwitchA] interface tunnel 1

[*SwitchA-Tunnel1] tunnel-protocol gre

[*SwitchA-Tunnel1] ip address 192.0.2.1 255.255.255.252

[*SwitchA-Tunnel1] source 192.0.254.1

[*SwitchA-Tunnel1] destination 192.0.255.1

[*SwitchA-Tunnel1] quit

PONTA B

[~SwitchA] interface tunnel 1

[*SwitchA-Tunnel1] tunnel-protocol gre

[*SwitchA-Tunnel1] ip address 192.0.2.2 255.255.255.252

[*SwitchA-Tunnel1] source 192.0.255.1

[*SwitchA-Tunnel1] destination 192.0.254.1

[*SwitchA-Tunnel1] quit


########## CONFIGURAR SNMP NO SWITCH HUAWEI S6720S-26Q-EI-24S-AC ##########

######## Explicação de cada campo ########

<huawei> system-view ----> Entrar em modo conf

[huawei]snmp-agent ---> Entrar no modo de conf do snmp

[huawei]snmp-agent community read cipher nome da community ---> configurar a community e criptografar o nome configurado

[huawei]snmp-agent sys-info version v2c --> Configurar versão do protocolo

[huawei]snmp-agent target-host trap address udp-domain 192.0.2.1 udp-port 161 params securityname cipher nome da community 

--> Configurar qual ip tem acesso ao equipamento 

[huawei]snmp-agent trap enable --> Habilitando as consultas ao equipamento

########## CONFIGURAR SNMP EM RULE NO SWITCH HUAWEI S6720S-26Q-EI-24S-AC ##########

<HUAWEI> system-view

[HUAWEI] acl 2000

[HUAWEI-basic-2000] rule permit source 192.168.10.10 0

[HUAWEI-basic-2000] quit

[HUAWEI] snmp-agent acl 2000


######## Configuração dos campos acima explicados ########

<huawei> system-view

[huawei]snmp-agent

[huawei]snmp-agent community read cipher nome da community

[huawei]snmp-agent sys-info version v2c 

[huawei]snmp-agent target-host trap address udp-domain 192.0.2.1 udp-port 161 params securityname cipher nome da community

[huawei]snmp-agent trap enable

######## Acesso padrão Switch huawei modelo: S5720-32X-EI-24S-AC via console-serial ########

********** Usuário: admin Senha: admin@huawei

######## Desabilitando auto negociação nas portas do Switch huawei modelo: S5720-32X-EI-24S-AC ########

********** undo negotiation auto

######## Acesso padrão Switch huawei modelo: S6730-H24X6C via console-serial ########

********** Usuário: admin Senha: admin@huawei.com 

######## Resetar contadores da porta no switch huawei ########

********** reset counters interface XGigabitEthernet 0/0/2

######## Verificar os logs do Switch Huawei ########

********** display logbuffer

######## Configurar porta do Switch Huawei como porta l3 ########

********** undo portswitch

********** interface vlanif númerodavlan

######## Limpar estatisticas de erro da interface no switch huawei S5720-32X-EI-24S-AC ########

******** reset counters interface XGigabitEthernet 0/0/2

######## Exibir histórico dos comandos que foi digitado no equipamento ########

******** display history-command all-users

######## Configurar community em um peer bgp no HUAWEI S6720S-26Q-EI-24S-AC  ########

******** Configurar a route-policy com os devidos parâmetros ********

route-policy NOME-DA-POLICY permit node NÚMERO-DO-NODE

description DESCRIPTION-DA-POLICY

if-match ip-prefix NOME-DA-PREFIXLIST

apply community XXXXX:YYYYY

******** Na instância do BGP configurar os parâmetros *********

peer X.X.X.X enable
  
peer X.X.X.X route-policy NOME-POLICY-IMPORT import

peer X.X.X.X route-policy NOME-POLICY-EXPORT export

peer X.X.X.X advertise-community

########## Habilitar ipv6 nainterface como undo portswitch no switch HUAWEI S6720S-26Q-EI-24S-AC ##########

<huawei> system-view ----> Entrar em modo conf

[huawei] ipv6

[huawei]interface interface-type interface-number

[huawei] ipv6 enable

Link de referência do Fabricante

https://support.huawei.com/enterprise/en/doc/EDOC0100533708?section=j00b

Ipv6 Huawei

https://support.huawei.com/enterprise/br/doc/EDOC1100074755/e6ca48ed/basic-ipv6-configuration-commands#EN-US_CLIREF_0139428486

########## Verificar se o protocolo ipv6 está ativo na interface ##########

display ipv6 interface interface-type interface-number

########## Transformar porta de switch em porta de router L3 ##########

<huawei> system-view ----> Entrar em modo conf

[huawei] interface interface-type interface-number

[huawei] undo portswitch

Obs. Se ao digitar o comando dê o erro de VCMP. Digite o segunte comando na porta: vcmp role server 

########## Habilitar para que o roteador/switch não faça checagem do as-path (Utilizado principalmente em IX (Internet exchange)) ##########

<huawei> system-view ----> Entrar em modo conf

[huawei] bgp número-do-asn

[huawei] undo chck-first-as

Referência do Fabricante

https://support.huawei.com/enterprise/en/doc/EDOC1100116542/15b843f2/check-first-as

########## Desabilitar tela inicial de troca de senha Huawei ##########

<Huawei> system-view

[Huawei] aaa

[Huawei-aaa] local-aaa-user password policy administrator

[Huawei-aaa-lupp-admin]undo password alert original

Refereência do fabricante.

https://support.huawei.com/enterprise/en/knowledge/EKB1100014967


########## Verificar clientes conectados no radius ##########

display access-user authen-method radius

########## Verificar cliente especifico no radius com detalhes ##########

display access-user authen-method radius username nomedousuáriopppoe verbose


## Lista quantidade de clientes no caixa "slot"

display pppoe statis slot " "

## Nat 

display nat user-information slot " " verbose

display nat user-information slot " " verbose | count 

display nat session table 

display nat session table verbose

display nat memory-usage session 

display nat memory-usage user-information

## CPU 

display health

display memory-usage

# Comandos pppoe


# MOSTRA TODOS USUARIOS CONECTADOS, MAC, USER, IP, INTERFACE
dis access-user interface GigabitEthernet 0/3/11.2000 


dis access-user interface Eth-Trunk12.4093 summary 


display pppoe statistics interface Eth-Trunk12.4093



display aaa online-fail-record


# derrubar:
aaa
    cut access-user username allison71 all
#

# limpar lista de falhas:
run reset aaa online-fail-record



















