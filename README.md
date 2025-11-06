# 🚀 Alerta de Estoque: Automação Condicional (n8n)

Este projeto demonstra um workflow robusto e seguro construído com **n8n** para simular o monitoramento de inventário em tempo real. O foco é a aplicação de **lógica condicional (IF)** para classificar produtos com **Estoque Crítico** e direcionar ações de notificação ou registro de forma autônoma.

É um excelente exemplo de **Data Pipeline** focado em processamento, filtragem e decisão.

---

## ✨ Destaques do Projeto e Habilidades Demonstradas

Este workflow valida a proficiência nas seguintes áreas de automação:

* **Arquitetura de Fluxo:** Criação de um pipeline completo: **Ingestão (API) → Manipulação → Lógica (IF) → Ações (Mocking)**.
* **Manipulação de Dados Essencial:** Uso combinado e estratégico dos nós `Edit Fields (Set)` e `Rename Keys` para:
    * **Limpeza de Dados:** Remoção de campos irrelevantes da API de origem.
    * **Geração de Dados:** Criação de campos dinâmicos (`EstoqueAtual`) com expressões JavaScript (`Math.random()`).
* **Lógica Condicional (IF Node):** Implementação de uma regra de **"Estoque Crítico"** (`EstoqueAtual < 10`) que bifurca o fluxo em rotas de alta e baixa prioridade.
* **Melhores Práticas (Mocking):** Uso de nós `NoOp` (simulação) para substituir conexões reais de e-mail e planilhas, permitindo que o projeto seja **100% público e seguro** no GitHub.

---

## ⚙️ Arquitetura Detalhada do Workflow

O fluxo processa itens da API (`jsonplaceholder`) e os divide em duas ações finais.

| Bloco (Node) | Nome no Workflow | Função e Lógica Aplicada |
| :--- | :--- | :--- |
| **Gatilho** | `When clicking 'Execute workflow'` | Simula um gatilho manual para iniciar a automação. |
| **Fonte** | `HTTP Request` | Busca 100 registros fictícios (produtos) de uma API pública. |
| **Manipulação** | `Edit Fields` | Cria o campo `EstoqueAtual` (valor aleatório 1-50) e extrai o `ID_Produto`. |
| **Limpeza** | `Rename Keys` | **Filtra e limpa** o fluxo, mantendo apenas os campos `ID_Produto` e `EstoqueAtual`. |
| **Decisão** | `IF` | Lógica: Se `EstoqueAtual` é **menor que 10**, segue para o caminho **TRUE** (Alerta). |
| **Ação TRUE** | `Mock_Email_Alerta_Estoque` | **Alerta Urgente:** Simula o envio de e-mail/Slack para a equipe de reposição. |
| **Ação FALSE** | `Mock_Sheets_Registro_OK` | **Registro Normal:** Simula o armazenamento em um banco de dados/planilha. |

---

## 🛠️ Como Instalar e Testar o Projeto

1.  **Download:** Baixe o arquivo JSON limpo (`Alerta_Estoque_Automacao_n8n.json`) deste repositório.
2.  **Importação:** No seu ambiente n8n, clique em **File > Import from JSON** e carregue o arquivo.
3.  **Teste:** Clique no botão **`Execute Workflow`** no canto inferior.

### Resultado Esperado

Após a execução, observe o nó **IF**:

* O número de itens nos caminhos **TRUE** e **FALSE** (os nós `Mock_...`) mudará a cada execução, confirmando que a lógica condicional está funcionando corretamente com dados dinâmicos.

---

## 📄 Licença

Este projeto está sob a **[MIT License](LICENSE)**. Sinta-se à vontade para usar, modificar e distribuir o código.

---

