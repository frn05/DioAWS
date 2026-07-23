# ☁️ IaC para Modelos Preditivos: AWS CloudFormation & Amazon Forecast

Este repositório contém a documentação e o código desenvolvidos durante o desafio da [DIO](https://www.dio.me/), focado na implementação de uma infraestrutura automatizada na nuvem utilizando **AWS CloudFormation**.

O projeto foi desenhado para preparar o ambiente necessário para a ingestão de dados e treinamento de modelos de aprendizado de máquina através do **Amazon Forecast**.

## 🎯 Objetivo do Desafio

Aplicar conceitos de **Infraestrutura como Código (IaC)** para automatizar a criação de recursos essenciais em projetos de Data Science e Machine Learning na nuvem, garantindo rastreabilidade, documentação estruturada e versionamento via GitHub.

---

## 🧠 Conceitos e Insights Adquiridos

Durante o desenvolvimento desta stack, aprofundei os seguintes conceitos técnicos:

* **Infraestrutura como Código (IaC):** Automatização do provisionamento de recursos, transformando configurações complexas (que exigiriam dezenas de cliques no console) em scripts rastreáveis e versionáveis.
* **Amazon Forecast & Integração de Dados:** Entendimento de que modelos preditivos na AWS exigem uma arquitetura de dados subjacente segura. O Forecast não armazena os dados primários; ele precisa extraí-los de um repositório central.
* **IAM Roles e o Princípio do Menor Privilégio:** A criação de uma função (`AWS::IAM::Role`) específica para o serviço `forecast.amazonaws.com`. Em vez de dar acesso irrestrito, a política foi formatada para permitir operações de leitura e gravação estritamente no Bucket S3 criado na mesma stack, garantindo segurança na manipulação de datasets de treinamento.

---

## 🛠️ Arquitetura da Solução

O arquivo `forecast-infra.yaml` provisiona os seguintes componentes:

1.  **Amazon S3 Bucket:** O data lake inicial. Um repositório preparado (com versionamento ativo) para o armazenamento de arquivos CSV contendo as séries temporais que alimentarão algoritmos de previsão.
2.  **IAM Execution Role:** A identidade de segurança. Permite que o serviço Amazon Forecast assuma as credenciais corretas para ler os arquivos de dados brutos no S3 e, posteriormente, exportar as previsões e métricas do modelo gerado.

---

## 🚀 Passo a Passo de Execução

Para implantar esta arquitetura na sua conta AWS:

1. Acesse o [AWS Management Console](https://console.aws.amazon.com/).
2. Navegue até o serviço **CloudFormation**.
3. Clique em **Create stack** (With new resources).
4. Selecione **Upload a template file** e envie o arquivo `forecast-infra.yaml` deste repositório.
5. Nomeie a stack (ex: `ForecastDataPipeline`).
6. Na última tela de revisão, marque a caixa que diz: **I acknowledge that AWS CloudFormation might create IAM resources.** (Isso é obrigatório pois nosso script cria uma role de segurança).
7. Clique em **Submit**.
8. Vá na aba **Outputs** da sua stack concluída para visualizar o ARN da Role e o nome do Bucket gerados. Agora, o ambiente está pronto para conectar um dataset em Python ou via console e iniciar o treinamento no Amazon Forecast!

> **⚠️ Destruindo a Stack:** Lembre-se de deletar a Stack após os estudos para evitar custos. Importante: O Bucket S3 deve estar vazio antes da exclusão da stack.

---

## 📚 Referências Oficiais

* [Tutorial CloudFormation - Criar os perfis e as políticas do Amazon Forecast](https://docs.aws.amazon.com/pt_br/forecast/latest/dg/tutorial-cloudformation.html)
