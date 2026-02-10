================================================================================
           MANUAL DO USUÁRIO E DOCUMENTAÇÃO TÉCNICA
================================================================================

1. INTRODUÇÃO
A TOPOMIR Network Toolkit Pro é uma aplicação projetada para administradores de 
redes e engenheiros de infraestrutura. Ela consolida cálculos de sub-redes, 
simulações de rádiofrequência (WiFi), análise de agregação de links (LACP) e 
conformidade de segurança VPN.

--------------------------------------------------------------------------------
2. GUIA DE OPERAÇÃO DOS MÓDULOS
--------------------------------------------------------------------------------

2.1 DESCOBERTA DE ENDEREÇO & WILDCARD
- O que faz: Identifica a rede, broadcast e máscara wildcard de um IP.
- Como usar: Digite o IP com a máscara CIDR (ex: 192.168.1.50/24).
- Utilidade: Fornece a Wildcard Mask, essencial para configurar ACLs (Access 
  Control Lists) em roteadores Cisco e outros dispositivos de borda.

2.2 DHCP LEASE TIME CONVERTER
- O que faz: Converte tempos de aluguel (dias, horas, minutos) em segundos totais.
- Como usar: Insira o tempo desejado e gere o valor.
- Utilidade: Facilita a configuração de servidores DHCP Linux/Windows que 
  exigem o tempo de "Lease" no formato de segundos.

2.3 PLANEJADOR DE SUB-REDES
- O que faz: Divide um bloco IP principal em sub-redes menores.
- Como usar: Informe o IP base, a máscara original e a quantidade de sub-redes.
- Utilidade: Auxilia no planejamento de VLSM (Variable Length Subnet Masking).

2.4 WIFI RF BUDGET (ANÁLISE DE SINAL)
- O que faz: Simula a força do sinal (RSSI) baseada em distância e obstáculos.
- Como usar: Selecione a frequência (2.4, 5 ou 6GHz), a distância e adicione
  as barreiras (paredes, portas, etc) presentes no ambiente.
- Status do Sinal:
  * Acima de -67 dBm: Sinal Excelente (Voz/Vídeo 4K).
  * -67 a -75 dBm: Sinal Bom (Navegação geral).
  * Abaixo de -85 dBm: Sem conexão estável.

2.5 LACP / ETHERCHANNEL ADVANCED
- O que faz: Calcula a vazão real de links agregados (Bonding).
- Como usar: Defina o número de links e o método de Hash (L2, L3 ou L4).
- Nota: A eficiência varia conforme o método de balanceamento.

2.6 SEGURANÇA VPN & HASH ANALYZER
- O que faz: Avalia o nível de segurança de túneis IPsec e gera senhas (PSK).
- Como usar: Selecione os algoritmos de criptografia e Hash.
- Veredito: O sistema classifica a conexão de "Insegura" a "Military Grade".

--------------------------------------------------------------------------------
3. FUNDAMENTOS DOS CÁLCULOS E BASES NORMATIVAS
--------------------------------------------------------------------------------

Os valores e fórmulas aplicados nesta ferramenta não são arbitrários; eles seguem
padrões internacionais de engenharia e telecomunicações:

A. MATEMÁTICA DE REDES (IP/SUB-REDES)
- Fonte: RFC 791 (IPv4) e RFC 4632 (CIDR).
- Cálculo: Utiliza operações bitwise (AND/OR/NOT) sobre inteiros de 32 bits.
- Rede = IP AND Mascara.
- Broadcast = Rede OR (NOT Mascara).

B. RÁDIOFREQUÊNCIA E ATENUAÇÃO (WIFI)
- Fonte: Modelo de Propagação de Espaço Livre (FSPL) e Padrão IEEE 802.11.
- Fórmula (Friis): Perda = 20 log10(distância) + 20 log10(frequência) - 27.55.
- Atenuação de Obstáculos: Valores de perda (-3dB a -20dB) baseados nos manuais 
  de Site Survey da Cisco e Aruba Networks para diferentes materiais (Concreto, 
  Vidro, Metal).

C. AGREGAÇÃO DE LINKS (LACP)
- Fonte: IEEE 802.3ad (atualmente 802.1AX).
- Coeficientes: A eficiência de 70% a 96% reflete a distribuição estatística de 
  tráfego real em métodos de Hash por IP e Portas (Camada 3 e 4).

D. SEGURANÇA E CRIPTOGRAFIA (VPN)
- Fonte: NIST (National Institute of Standards and Technology) e RFC 8221.
- Classificação: Segue as recomendações do NIST sobre o fim da vida útil de 
  algoritmos como MD5, 3DES e DH Grupos menores que 14, considerados vulneráveis 
  a ataques modernos de força bruta.

--------------------------------------------------------------------------------
4. DICAS TÉCNICAS
--------------------------------------------------------------------------------
- Use sempre o botão de cópia rápida para evitar erros de digitação de IPs.
- Em projetos WiFi, lembre-se que o sinal de 5GHz sofre maior atenuação por 
  obstáculos físicos do que o de 2.4GHz.
- Para máxima segurança em VPNs, prefira algoritmos AES-GCM e DH Group 19 ou 21.

================================================================================
                     FIM DA DOCUMENTAÇÃO - TOPOMIR 2026
================================================================================
