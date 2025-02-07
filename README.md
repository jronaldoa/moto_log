Descrição do Projeto
O MotoLog é um sistema projetado para motocicletas, que registra e armazena informações de localização (via GPS) e nível de suspensão (via potenciômetro). O sistema é capaz de registrar dados importantes, como as coordenadas geográficas e os valores de inclinação das suspensões dianteira e traseira da motocicleta. Além disso, ele faz uso de um cartão SD para armazenar os dados em formato CSV, facilitando a análise posterior. O sistema também integra o sensor MPU6050 para medir a inclinação e sensores de posição para obter os valores de ajuste de suspensão.

Funcionalidades
Leitura de GPS: O sistema registra latitude e longitude da moto a cada intervalo, utilizando o módulo GPS.
Leitura de Suspensão: O sistema monitora o nível de suspensão dianteira e traseira usando potenciômetros.
Registro no Cartão SD: Os dados são armazenados em um cartão SD em formato CSV, incluindo hora, latitude, longitude, e valores de inclinação e ajuste de suspensão.
Calibração: O sistema permite recalibrar os potenciômetros para zerar os valores.
Inclinação: O sistema lê a inclinação da moto em dois eixos (X e Y) com o sensor MPU6050.
Componentes Utilizados
Arduino Mega 2560
Módulo GPS (TinyGPS++)
MPU6050 (Sensor de inclinação)
Potenciômetro para ajuste da suspensão
Cartão SD para armazenamento
Display Serial para feedback
Estrutura de Dados
Os dados coletados são gravados no cartão SD em formato CSV, com as seguintes colunas:

Hora: Hora de gravação (HH:MM:SS)
Latitude: Latitude da motocicleta (com 6 casas decimais)
Longitude: Longitude da motocicleta (com 6 casas decimais)
SensorD: Valor de suspensão dianteira (em %)
SensorT: Valor de suspensão traseira (em %)
Inc. Tras/Frente: Inclinação do eixo X (sensor MPU6050)
Inc. Direita/Esquerda: Inclinação do eixo Y (sensor MPU6050)
Funcionalidades do Código
Leitura de GPS: O código lê as coordenadas de latitude e longitude a cada 2 segundos e as armazena.
Leitura de Suspensão: O código lê os valores dos potenciômetros para frente e traseiro da motocicleta, com a possibilidade de calibração dos sensores.
Registro no SD: Cada dado coletado (hora, posição, inclinação e sensores de suspensão) é registrado no arquivo datalog.csv no cartão SD.
Inclinação (MPU6050): O sistema captura a inclinação da moto nos eixos X e Y, fornecendo informações sobre o nível de inclinação.
Fluxo do Sistema
Inicialização:

O sistema configura o módulo GPS e o MPU6050.
O cartão SD é inicializado para gravação de dados.
Leitura dos Dados:

A cada 200 ms, o sistema lê os valores dos potenciômetros para as suspensões dianteira e traseira.
A cada 2 segundos, o sistema lê a posição GPS da motocicleta.
A cada 200 ms, os dados de inclinação são obtidos do sensor MPU6050.
Armazenamento:

Todos os dados são registrados no arquivo CSV no cartão SD.
Reset de Posição:

O botão de reset (conectado ao pino 2) permite zerar os valores dos potenciômetros de suspensão.
Como Usar
Conexões:

Conecte os potenciômetros ao Arduino (pinos analógicos A0 e A1).
Conecte o módulo GPS ao pino Serial1.
Conecte o sensor MPU6050 ao barramento I2C.
Conecte o cartão SD ao pino chipSelect (pino 53 no Arduino Mega).
Iniciar o Sistema:

Após ligar o Arduino, o sistema começará a ler dados de GPS, suspensão e inclinação.
O sistema gravará os dados automaticamente no cartão SD a cada intervalo configurado.
Visualização dos Dados:

Você pode abrir o arquivo datalog.csv no seu computador para visualizar os dados registrados.
Resetar os Valores de Suspensão:

Para calibrar os potenciômetros de suspensão, basta pressionar o botão de reset. O sistema irá zerar os valores.

