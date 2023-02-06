# IC-PPM (Passivity Phase Margin)
Arquivos usados na pesquisa e "linha de raciocínio" do projeto.

## Objetivos

## Visão Geral do Projeto e Pacotes de Trabalho:
- Construir uma simulação do projeto a fim de encontrar uma Função de Transferência que descreva seu comportamento;
- Criar um diagrama de blocos em malha fechada do sistema;
- Linearizar;
- Entender e aplicar a Passivity Phase Margin;
- Aplicar no exoesqueleto e testar;
- Comparar os dados e analisar os resultados.

## Atualizações sobre o Projeto:

### 11 de janeiro
Foram realizadas mudanças no arquivo da simulação (modelo), pois não estava funcionando => o PID não mandava o sinal de corrente para a fonte.
O controlador não faz sentido => é necessário subtrair o torque medido da referência e aplicar uma função transferência que gere os sinais de corrente que a fonte de corrente exige a partir do erro em **Nm**.
Falei com o Leo sobre a FT.

### 01 de fevereiro
Realizei novas mudanças no modelo, pois não fazia sentido a entrada de corrente e potência no controlador PID, se utilizamos o torque.
Elisa passou alguns insights sobre o modelo.
**FT:** a função transferência deve relacionar a corrente necessária para o motor realizar o torque desejado => ela "entra" entre o controlador e a fonte de corrente.

### 06 de fevereiro
Tive uma reunião com o Leo e consegui entender bem melhor alguns aspectos do projeto e o que é necessário na simulação.
O mais importante agora é focar na modelagem e esquecer um pouco da parte de controle do projeto.
O motor do exoesqueleto já possui algumas camadas de controle => controladores eletrônicos com loops de controle.
Faltam etapas no SimuLink entre o controlador e o motor em si.
Preciso dos ganhos PI desses controladores => adicionar as etapas que faltam => malha de controle "duplo", com comtrolador PI de velocidade e um controlador PI de corrente, no qual o controlador de velocidade serve como referência para o de corrente também.
Costuma-se usar o exo como  fonte de velocidade.
