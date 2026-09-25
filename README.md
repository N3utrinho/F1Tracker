F1Tracker
O F1Tracker é um projeto focado no processamento de dados de telemetria de código aberto da Fórmula 1 utilizando Python e a biblioteca fastf1. O objetivo central é criar ferramentas analíticas essenciais para a engenharia de pista, entendendo através de dados exatamente onde o tempo de volta pode ser otimizado.

Esta análise prática foca em quatro métricas específicas de performance:

O DeltaT entre duas voltas.

O posicionamento no ápice da curva.

Os pontos de frenagem e liberação do freio.

A velocidade mínima durante o contorno das curvas.

Com essas informações fundamentadas em dados reais das corridas, é possível determinar e comparar as melhores decisões e estratégias de pilotagem em cada circuito.

⚙️ Configuração do Ambiente
Para garantir estabilidade e evitar bloqueios ou sobrecargas comuns em plataformas na nuvem (como o Google Colab), este projeto foi estruturado para rodar localmente na sua máquina utilizando o Jupyter Notebook.

Passo a Passo
Abra o Prompt de Comando (CMD) ou o terminal do seu computador.

Instale as dependências necessárias:

Bash
pip install fastf1 pandas matplotlib notebook
Nota: O download e a instalação dos pacotes podem levar alguns minutos, dependendo da velocidade da sua internet.

Crie e acesse a pasta do projeto:

Bash
mkdir ProjetoF1
cd ProjetoF1
Inicie o ambiente virtual:

Bash
jupyter notebook
O seu navegador padrão (Chrome, Safari, etc.) abrirá automaticamente a interface do Jupyter (geralmente no endereço localhost:8888).

Crie um novo script: Vá em New (Novo) > Notebook e selecione o kernel Python 3. Cole o código base na célula de execução.

🧠 Funcionamento do Código
Abaixo está o detalhamento de como o script estrutura e processa a telemetria.

Importações e Otimização de Cache
Python
import fastf1
import fastf1.plotting
import matplotlib.pyplot as plt
import os

os.makedirs('cache', exist_ok=True)
fastf1.Cache.enable_cache('cache')
O código carrega as bibliotecas necessárias para manipulação de dados dinâmicos e plotagem. A configuração de cache cria uma pasta local para salvar a corrida no seu PC, evitando que o computador precise se conectar aos servidores e baixar centenas de megabytes de dados novamente a cada execução.

Carregamento da Sessão
Python
sessao = fastf1.get_session(2023, 'Brazil', 'Q')
sessao.load()
Ao executar este comando, o computador acessa a internet e baixa os dados da etapa definida pelos parâmetros: Ano (Ex: 2023), Localidade (Ex: Brazil) e Tipo de Sessão ('Q' para Qualificação, 'R' para Corrida, 'FP1', 'FP2', 'FP3' para Treinos Livres).

Filtragem e Isolação de Voltas
Python
volta_1 = sessao.laps.pick_driver(corredor_1).pick_fastest()
volta_2 = sessao.laps.pick_driver(corredor_2).pick_fastest()
O FastF1 utiliza a sigla oficial de três letras para identificar os pilotos. Como eles completam várias voltas durante uma qualificação, esse comando atua como um funil: ele vasculha os tempos totais e isola automaticamente apenas a volta mais rápida (menor tempo) de cada piloto escolhido.

Extração da Telemetria
Python
tel_1 = volta_1.get_telemetry()
tel_2 = volta_2.get_telemetry()
Esse comando extrai os dados físicos da volta isolada. Ele devolve uma tabela detalhada onde cada linha representa uma fração de segundo e as colunas armazenam as variáveis dinâmicas do veículo. Você passa a ter acesso a canais fundamentais para análise:

Speed: Velocidade instantânea em km/h.

Throttle: Porcentagem de aplicação do acelerador (0 a 100%).

Brake: Acionamento e pressão do sistema de freios.

nGear: Marcha engatada no momento.

X, Y, Z: Coordenadas espaciais do GPS para mapear a trajetória.

Visualização e Comparativo (DeltaT)
O trecho final do script utiliza o matplotlib para gerar um gráfico bidimensional (Distância em metros vs. Velocidade em km/h). Em seguida, ele extrai o tempo total de cada volta usando .total_seconds(), imprime os tempos separadamente no terminal e utiliza uma lógica condicional (if/elif/else) para calcular o delta (a diferença exata de tempo) e demonstrar qual piloto foi o mais rápido.

🏎️ Guia de Referência
Para utilizar o script corretamente, você precisará informar as siglas dos pilotos no terminal e ajustar o local da corrida diretamente no código base.

🪪 Pilotos (Abreviação de 3 Letras)
Insira a sigla exata (TLA) quando o prompt do terminal solicitar o corredor.

Red Bull: VER (Max Verstappen) | PER (Sergio Pérez)

Ferrari: LEC (Charles Leclerc) | SAI (Carlos Sainz)

McLaren: NOR (Lando Norris) | PIA (Oscar Piastri)

Mercedes: HAM (Lewis Hamilton) | RUS (George Russell)

Aston Martin: ALO (Fernando Alonso) | STR (Lance Stroll)

Alpine: GAS (Pierre Gasly) | OCO (Esteban Ocon)

Williams: ALB (Alexander Albon) | SAR (Logan Sargeant) | COL (Franco Colapinto)

Haas: MAG (Kevin Magnussen) | HUL (Nico Hülkenberg) | BEA (Oliver Bearman)

RB / AlphaTauri: TSU (Yuki Tsunoda) | RIC (Daniel Ricciardo) | LAW (Liam Lawson)

Sauber / Alfa Romeo: BOT (Valtteri Bottas) | ZHO (Zhou Guanyu)

🌍 Locais das Corridas
Você pode alterar o local no código base, dentro da função fastf1.get_session(), usando o nome do país ou do circuito oficial em inglês. Escolha uma das opções abaixo:

Bahrain ou Sakhir

Saudi Arabia ou Jeddah

Australia ou Melbourne

Japan ou Suzuka

China ou Shanghai

Miami

Emilia Romagna ou Imola

Monaco

Canada ou Montreal

Spain ou Barcelona

Austria ou Spielberg

Great Britain ou Silverstone

Hungary ou Budapest

Belgium ou Spa

Netherlands ou Zandvoort

Italy ou Monza

Azerbaijan ou Baku

Singapore

USA ou Austin

Mexico ou Mexico City

Brazil ou Interlagos

Las Vegas

Qatar ou Lusail

Abu Dhabi ou Yas Marina
