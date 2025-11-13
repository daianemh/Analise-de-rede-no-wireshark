🦈 Análise de Tráfego de Rede com Wireshark

🌐 Ambiente Controlado

O estudo foi realizado em um ambiente controlado para fins de aprendizado e demonstração de técnicas de análise de rede.

🚀 Visão Geral do Projeto

Este repositório documenta uma análise prática de tráfego de rede capturado através da ferramenta Wireshark, o analisador de protocolo de rede padrão da indústria.

O objetivo principal desta análise foi:

    Capturar e Inspecionar pacotes em tempo real de uma interface de rede Wi-Fi (Wi-Fi 2).

    Identificar e Classificar os diferentes tipos de protocolos em uso (e.g., TCP, UDP, TLS, ARP).

    Demonstrar a utilidade do esquema de coloração do Wireshark para rápida identificação de fluxos de comunicação e potenciais problemas.


🎨 Legenda de Coloração do Wireshark

O Wireshark utiliza cores para categorizar e destacar pacotes, tornando a análise mais eficiente.
Cor	Significado	Exemplo de Uso
🔵 Azul Claro	Pacotes de Resposta (Sucesso). O pacote foi recebido com sucesso. Cor mais comum no tráfego normal.	Comunicação HTTP/DNS bem-sucedida.
⚫ Azul Escuro	Pacotes de Requisição ou Confirmação. Indicam o envio de dados ou o início de uma conexão.	Primeiro pacote de um handshake TCP.
🟢 Verde	Início e Fim de Conexões TCP. Sinalizam o handshake inicial (SYN) e a finalização da conexão (FIN).	Conexão estabelecida e encerrada.
🔴 Vermelho	Problema ou Erro Crítico. Indica problemas como erro de checksum, pacote perdido, ou retransmissão excessiva. Sempre exige investigação.	Pacotes Bad TCP ou ICMP Destination Unreachable.
🟡 Amarelo	Pacotes UDP (User Datagram Protocol). Protocolo mais rápido, mas não garante a entrega.	Serviços de streaming de vídeo, VoIP, jogos.
🌸 Rosa	Pacotes ARP (Address Resolution Protocol). Usado na rede local para descobrir o endereço MAC de um IP conhecido.	O seu computador perguntando: "Quem é o IP 192.168.0.1?".
⚪ Cinza	Pacotes que estão fora de uma conversa principal ou que não pertencem ao filtro de busca.	Tráfego lateral ou irrelevante para a análise focada.

📸 Análise Passo a Passo (Screenshots)

Os screenshots abaixo ilustram o processo de captura e os resultados da análise.

1. Seleção da Interface e Início da Captura

<img width="716" height="606" alt="image" src="https://github.com/user-attachments/assets/2d69d9df-28f6-4849-bde0-8364dd0614e3" />



    Descrição: Captura da tela inicial mostrando a seleção da interface de rede (Wi-Fi 2) para a escuta. O Wireshark 4.4.9 está pronto para iniciar a coleta de pacotes.

        Neste passo, definimos "o que" e "de onde" queremos ouvir na rede.

2. Tráfego Capturado em Tempo Real

<img width="716" height="603" alt="image" src="https://github.com/user-attachments/assets/ae9c343b-5898-433b-a5ba-3d6e6bd90d68" />

<img width="859" height="632" alt="image" src="https://github.com/user-attachments/assets/3cac4401-7072-4668-bca3-052b29582afb" />

    Descrição: Visualização principal dos pacotes sendo capturados. A lista de pacotes exibe protocolos comuns em redes modernas:

        QUIC: Protocolo de transporte usado por serviços como Google/Chrome.

        TLSv1.2: Protocolo de segurança (HTTPS).

        ARP (Rosa): Comunicação para resolução de endereços locais.

        A coluna Protocolo permite identificar rapidamente o tipo de comunicação em andamento.

3. Foco em Conexão Segura (TLS) e Problema (Vermelho)
<img width="845" height="648" alt="image" src="https://github.com/user-attachments/assets/8145a26d-4fb8-4a75-83a0-f79bfbd39c2f" />

    Descrição: Uma inspeção mais detalhada de um segmento da captura.

        Linha Vermelha (#12): Um pacote TCP marcado em Vermelho (e destacado na imagem) indica uma anomalia ou problema de fluxo que requer atenção imediata.

        Painel Inferior: O pacote selecionado (que não é o vermelho) é um TLSv1.2 de origem 179.189.48.162 (servidor externo) para o host local, usando a porta de segurança 443 (HTTPS).

        O painel inferior mostra o encapsulamento do pacote, camada por camada (Ethernet II > IPv4 > TCP > Transport Layer Security).

4. Detalhe de um Pacote com Erro

<img width="1081" height="621" alt="image" src="https://github.com/user-attachments/assets/0e17b921-bda3-4182-a832-69161bc283f9" />


    Descrição: Visualização detalhada de um pacote TCP específico, mostrando a estrutura de bytes brutos (Hex Dump).

        Destaque: O campo Coloring Rule Name: **Bad TCP** confirma que o pacote foi automaticamente sinalizado pelo Wireshark devido a um erro na análise de seu cabeçalho ou fluxo TCP, reforçando o uso da cor Vermelha como alerta.

        Isso demonstra como o Wireshark não apenas captura, mas também realiza uma análise de integridade básica dos protocolos.
## 🧑‍💻 Autor

* **Nome:** Daiane M. Horbach
* **LinkedIn:** www.linkedin.com/in/daiane-moreira-horbach
