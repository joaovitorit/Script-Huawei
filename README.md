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









