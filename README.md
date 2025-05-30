# 🏗️ Automação de Processamento de Pedidos - UiPath

Este projeto desenvolvido em **UiPath** tem como objetivo automatizar o processamento de uma planilha de pedidos, realizando validação de dados, processamento simulado e envio de relatório final por e-mail.

---

## 🚀 Funcionalidades

✔️ Leitura da planilha `Pedidos.xlsx`  
✔️ Envio de cada linha para uma **Fila no Orchestrator** (`FilaProcessamento`)  
✔️ Consumo dos itens da fila para:  
- ✅ Validação dos dados (Nome, Sexo, CPF, RG, Veículo, Placa e Renavan)  
- ✅ Verificar dados ausentes ou inválidos  
- ✅ Processamento simulado (Delay)  
✔️ Atualização da planilha com status:  
- `"Processado"` ou `"Não Processado"` + justificativa  
✔️ Geração de logs detalhados durante todo o processo  
✔️ Envio de e-mail com a planilha final em anexo, contendo no corpo a quantidade de pedidos processados com sucesso  

---

## 📂 Estrutura do Projeto
    📦 FilaPedidos
    ┣ 📄 ProcessamentoPedidos.xaml
    ┣ 📄 ProcessarFila.xaml
    ┣ 📄 Pedidos.xlsx
    ┣ 📄 README.md


## 🧠 Lógica da Automação

### 1️⃣ **ProcessamentoPedidos.xaml**  
- Leitura da planilha `Pedidos.xlsx`  
- Envio de cada linha para a fila no Orchestrator (`FilaProcessamento`)  

### 2️⃣ **ProcessarFila.xaml**  
- Consome os itens da fila  
- Realiza validações:
  - CPF, RG, Placa e Renavan  
- Marca como:
  - `"Processado"` caso dados estejam válidos  
  - `"Não Processado"` com justificativa caso haja erro  
- Simula processamento (Delay de 2 segundos)  
- Atualiza a planilha com os resultados  
- Envia um e-mail com a planilha atualizada em anexo, informando no corpo a quantidade de pedidos processados com sucesso  

---

## ⚠️ Atenção antes de executar

✔️ Verifique os seguintes pontos antes de rodar o projeto:

1. 🔗 **Orchestrator:**  
- A fila **`FilaProcessamento`** precisa estar criada no Orchestrator.  
- Verifique se sua conexão Robot-Orchestrator está ativa.

2. 📧 **Configuração de E-mail:**  
- O projeto usa envio de e-mail via **Outlook**
- Você deve alterar dentro da atividade **`Send Email`**  a seguinte informação:  
   - **Para:** Destinatário desejado
     
3. 📄 **Local da Planilha:**  
- O caminho padrão da planilha é:  
`...\FilaPedidos\Pedidos.xlsx`  
- Altere o caminho nas atividades `Read Range` e `Write Range` se estiver diferente no seu ambiente.

4. 💼 **Dependências:**  
- Verifique se as dependências estão atualizadas no projeto:  
  - UiPath.Excel.Activities  
  - UiPath.Mail.Activities  
  - UiPath.System.Activities  
  - UiPath.Orchestrator.Activities  

---

## 📑 Pré-requisitos

- UiPath Studio instalado  
- Conta no UiPath Orchestrator  
- Outlook configurado
- Fila criada no Orchestrator com nome exato: **`FilaProcessamento`**  
- Planilha `Pedidos.xlsx` dentro da pasta `FilaPedidos`  

---

## 🏃‍♂️ Como executar

1. Execute primeiro o arquivo:  
→ **`ProcessamentoPedidos.xaml`** → Adiciona os itens na fila

2. Em seguida execute:  
→ **`ProcessarFila.xaml`** → Faz todo o processamento, validação, atualização da planilha e envio de e-mail

---

## 📨 Resultado Final

- ✔️ Planilha `Pedidos.xlsx` atualizada com colunas adicionais de **Status** e **Justificativa**  
- ✔️ E-mail automático enviado com:  
   - 📎 A planilha em anexo  
   - 📄 Mensagem contendo a quantidade de pedidos processados com sucesso  

---


## 🧑‍💻 Autor

- Gabriel 🚀  
- Projeto criado durante o estágio para RPA, para estudo e prática de automação robótica de processos (RPA) utilizando UiPath.

---

## ⭐ Licença

Este projeto é livre para uso educacional e para fins de estudo.

