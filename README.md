🦈 Análise de Tráfego de Rede com Wireshark

🌐 Ambiente Controlado

O estudo foi realizado em um ambiente controlado para fins de aprendizado e demonstração de técnicas de análise de rede.  atividade realizada 29/08/2025

🚀 Visão Geral do Projeto

Este repositório documenta uma análise prática de tráfego de rede capturado através da ferramenta Wireshark, o analisador de protocolo de rede padrão da indústria.

O objetivo principal desta análise foi:

    Capturar e Inspecionar pacotes em tempo real de uma interface de rede Wi-Fi (Wi-Fi 2).

    Identificar e Classificar os diferentes tipos de protocolos em uso (e.g., TCP, UDP, TLS, ARP).

    Demonstrar a utilidade do esquema de coloração do Wireshark para rápida identificação de fluxos de comunicação e potenciais problemas.


📸 Análise Passo a Passo (Screenshots)

Os screenshots abaixo ilustram o processo de captura e os resultados da análise.

1. Seleção da Interface e Início da Captura


    Descrição: Captura da tela inicial mostrando a seleção da interface de rede (Wi-Fi 2) para a escuta. O Wireshark 4.4.9 está pronto para iniciar a coleta de pacotes.

        Neste passo, definimos "o que" e "de onde" queremos ouvir na rede.

2. Tráfego Capturado em Tempo Real



    Descrição: Visualização principal dos pacotes sendo capturados. A lista de pacotes exibe protocolos comuns em redes modernas:

        QUIC: Protocolo de transporte usado por serviços como Google/Chrome.

        TLSv1.2: Protocolo de segurança (HTTPS).

        ARP (Rosa): Comunicação para resolução de endereços locais.

        A coluna Protocolo permite identificar rapidamente o tipo de comunicação em andamento.

3. Foco em Conexão Segura (TLS) e Problema (Vermelho)


    Descrição: Uma inspeção mais detalhada de um segmento da captura.

        Linha Vermelha (#12): Um pacote TCP marcado em Vermelho (e destacado na imagem) indica uma anomalia ou problema de fluxo que requer atenção imediata.

        Painel Inferior: O pacote selecionado (que não é o vermelho) é um TLSv1.2 de origem 179.189.48.162 (servidor externo) para o host local, usando a porta de segurança 443 (HTTPS).

        O painel inferior mostra o encapsulamento do pacote, camada por camada (Ethernet II > IPv4 > TCP > Transport Layer Security).

4. Detalhe de um Pacote com Erro


    Descrição: Visualização detalhada de um pacote TCP específico, mostrando a estrutura de bytes brutos (Hex Dump).

        Destaque: O campo Coloring Rule Name: **Bad TCP** confirma que o pacote foi automaticamente sinalizado pelo Wireshark devido a um erro na análise de seu cabeçalho ou fluxo TCP, reforçando o uso da cor Vermelha como alerta.

        Isso demonstra como o Wireshark não apenas captura, mas também realiza uma análise de integridade básica dos protocolos.
## 🧑‍💻 Autor

* **Nome:** Daiane M. Horbach
* **LinkedIn:** www.linkedin.com/in/daiane-moreira-horbach
