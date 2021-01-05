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











