## Projeto F1Tracker

## Objetivo Geral:

O objetivo do projeto é processar dados de telemetria de código aberto da

Fórmula 1 usando Python e a biblioteca FastF1 para entender onde o tempo de volta pode ser ganho.

A análise prática foca em quatro métricas específicas:

- O DeltaT entre duas voltas

- O posicionamento no ápice da curva

- Os pontos de frenagem e liberação do freio

- A velocidade mínima durante o contorno das curvas

Para assim conseguir determinar, com meio de dados qual seria a melhor opção no momento de cada corrida

Independente do computador que for rodar o codigo, tem-se que ter as bibliotecas nescessaria para o funcionamento ideal do codigo, portanto:

CMD: pip install fastf1 pandas matplotlib

Aqui como sera feito em uma ambiente de testes, eu usarei o Google Colab

#A api do Google Colab está bloqueando formas de execuções que nao rodem em computadores locais, para evitar sobrecarga eu acho. Enfim, ao inves do Google Colab começarei a usar o Jupyter Notebook, que roda localmente na sua maquina, com apenas algumas linhas de codigos sem precisar instalar e configurar todo um sistema (Python no caso)

## Passo a Passo:

## 1. Abra o Prompt de Comando (CMD)

## 2. Instale as bibliotecas necessárias

pip install fastf1 pandas matplotlib notebook

- Nota: O computador vai baixar alguns arquivos. Pode demorar um pouco de acordo com a velocidade da Net

## 3. Crie uma pasta para o projeto

- Criar Pasta do Projeto:

mkdir ProjetoF1

- Entrar na Pasta

cd ProjetoF1 e aperte Enter .

## 4. Criação de um notebook no Jupyter


- Abrir o Jupyter jupyter notebook

- O navegador vai abrir a forma de pesquisa padrão do computador (Chrome, Safari, Opera, etc) (provavelmente no endereço localhost:8888 ).

- Vá em New (Novo) e escolha a opção Notebook (se ele perguntar qual é o Kernel, basta selecionar "Python 3").

- Cole o seu código dentro dessa caixa

## Funcionamento do Codigo:

fastfl

fastfl.plotting

matplotlib.pyplot plt

os

(Importa as bibliotecas nescessarias para a execução do codigo)

```
exist_ok=
(misc_mpl_mods=
```

(Cria uma pasta para salvar os dados no seu PC e não precisar baixar de novo)

(Carrega a Qualificação de Monza em 2023 (Ano; Localidade;

'Q'(Qualificatoria)'R'(Corrida) (FP1', 'FP2')(Treinos Livres))

(Depois o computador acessa a internet , se conecta ao servidores e baixa os dados nescessarios de acordo com os argumentos inseridos)

```
volta_rbr sessao.
volta_fer sessao.
```

(Funciona como um funil, onde antes a gente pegou os dados de toda a corrida, aqui é filtrado de acordo com os dados que a gente deseja comparar)


(Isola a volta mais rápida de cada piloto)

(Max Verstappen ('VER') e Charles Leclerc ('LEC'). O FastF1 sempre usa a sigla oficial de três letras de cada piloto)

(Como eles deram várias voltas durante a qualificação, esse comando vasculha os tempos e seleciona automaticamente apenas a volta mais rápida (aquela com o menor tempo) de cada um)

## ####Exemplos:

- VER - Max Verstappen

- LEC - Charles Leclerc

- HAM - Lewis Hamilton

- NOR - Lando Norris

- ALO - Fernando Alonso

- SAI - Carlos Sainz

- PER - Sergio Pérez

###########

(Puxa a telemetria)(extrai os dados físicos da volta que isolamos)

(O que ele devolve (e guarda nas variáveis tel_rbr e tel_fer ) é uma tabela detalhada onde cada linha é uma fração de segundo e as colunas são as variáveis dinâmicas do veículo)

Dentro dessa tabela gerada pelo código, você passa a ter acesso a canais fundamentais para a engenharia de pista:

- Speed: Velocidade instantânea em km/h.

- Throttle: Porcentagem de aplicação do acelerador (0 a 100%).

- Brake: Acionamento e pressão do sistema de freios.

- nGear: Marcha engatada no momento.

- X, Y, Z: Coordenadas espaciais do GPS para mapear a trajetória.


(Cria e plota o gráfico) (De disntacia (m) por Velocidade (Km/h)

(Layout do Grafico)

(Parte grafica pronta)

(Extrair o tempo total de cada volta)

(Mostra os tempos de cada um de forma separada)

```
( )
tempo_rbr < tempo_fer:
diferenca = tempo_fer - tempo_rbr
( diferenca
tempo_fer < tempo_rbr:
diferenca = tempo_rbr - tempo_fer
( diferenca
```

(Mostra a diferença de tempo entre cada um, e demonstra tambem quem foi o mais rapido)
