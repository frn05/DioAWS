# ☁️ Minha Primeira Stack com AWS CloudFormation

Este repositório contém a documentação e o código desenvolvidos durante o desafio prático da [DIO](https://www.dio.me/), focado na implementação da primeira stack utilizando o **AWS CloudFormation**.

## 🎯 Objetivo do Desafio

Aplicar conceitos de **Infraestrutura como Código (IaC)**, provisionando recursos na AWS de forma automatizada, documentando os processos técnicos e utilizando o GitHub para versionamento e compartilhamento do conhecimento.

---

## 🧠 Conceitos e Insights Adquiridos

Durante este laboratório, consolidei os seguintes conceitos fundamentais:

* **Infraestrutura como Código (IaC):** A capacidade de gerenciar e provisionar datacenters através de arquivos de definição legíveis por máquinas, em vez de configurações interativas manuais em interface gráfica.
* **AWS CloudFormation:** O serviço da AWS que permite modelar, provisionar e gerenciar recursos da AWS (e de terceiros) de maneira previsível e repetível.
* **Templates (Modelos):** Arquivos formatados em JSON ou YAML que descrevem os recursos que você deseja criar (neste laboratório, utilizei o formato YAML por ser mais amigável e legível).
* **Stacks (Pilhas):** Uma coleção de recursos da AWS que você pode gerenciar como uma única unidade. Se a criação da stack falhar, o CloudFormation faz um *rollback* automático (reverte o processo), garantindo que você não pague por recursos criados pela metade.

---

## 🛠️ O que foi construído?

Para este desafio, criei um template YAML (`primeira-stack.yaml`) que provisiona um **Amazon S3 Bucket** com a funcionalidade de *Versioning* (versionamento de arquivos) ativada.

**Por que um S3 Bucket?**

É um recurso excelente para entender a anatomia de um template CloudFormation (Seções `AWSTemplateFormatVersion`, `Description`, `Resources` e `Outputs`) sem a complexidade de pré-requisitos de rede (VPCs) ou segurança (KeyPairs) exigidos por instâncias EC2.

---

## 🚀 Passo a Passo de Execução

Se você deseja replicar esta infraestrutura na sua conta AWS, siga os passos:

1. **Pré-requisitos:** Ter uma conta ativa na AWS e fazer login no [AWS Management Console](https://console.aws.amazon.com/).
2. **Acessar o CloudFormation:** Na barra de pesquisa, busque por `CloudFormation` e clique no serviço.
3. **Criar a Stack:**
   * Clique no botão **Create stack** (With new resources).
   * Em *Prerequisite - Prepare template*, escolha **Template is ready**.
   * Em *Specify template*, escolha **Upload a template file**.
   * Faça o upload do arquivo `primeira-stack.yaml` deste repositório e clique em *Next*.
4. **Detalhes da Stack:**
   * Dê um nome para a sua Stack (ex: `StackDesafioDIO`).
   * Clique em *Next* nas telas seguintes, mantendo as configurações padrão.
5. **Implantação:**
   * Revise as informações e clique em **Submit**.
   * Aguarde alguns segundos enquanto a AWS lê seu código e cria a infraestrutura. O status mudará para `CREATE_COMPLETE`.
6. **Validação:** Acesse o painel do serviço **S3** e verifique que seu novo bucket foi criado com sucesso!

> **⚠️ Atenção (Limpeza):** Lembre-se de deletar a Stack após os estudos. Basta ir no painel do CloudFormation, selecionar a Stack e clicar em **Delete**. Isso destruirá os recursos criados e evitará cobranças indesejadas (o bucket precisa estar vazio para ser deletado).

---

## 📚 Referências Oficiais

* [Documentação AWS - Passo a passo: Conceitos básicos do CloudFormation](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/gettingstarted.walkthrough.html)
