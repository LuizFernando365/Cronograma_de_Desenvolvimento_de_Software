# 🧪 Documento de Testes, Qualidade e Homologação (Fase 4)

> 📥 **Download da Versão Oficial:** [Clique aqui para baixar o PDF completo da Fase 4](Documento_Fase4_Testes_e_Homologacao.pdf)  
> 🌐 **Ambiente de Homologação (Site Online):** [Acessar Loja Cyber Y2K Live](https://seu-site.vercel.app)

---

**Projeto:** Sistema de Gerenciamento e Vendas para Loja de Roupas (Cyber Y2K / Dark Streetwear)  
**Responsável:** Luiz  

---

## PARTE 1: RELATÓRIO DE COBERTURA DE TESTES

### 1. Plano e Estratégia de Testes
A estratégia de testes foi estruturada para cobrir os fluxos críticos de uso da loja virtual CYBER CULT, garantindo estabilidade, integridade das regras de negócio (RN) e proteção dos endpoints restritos do sistema.

---

### 2. Casos de Testes Funcionais Executados

| ID | Cenário / Funcionalidade | Passos do Teste | Resultado Esperado | Status |
| :--- | :--- | :--- | :--- | :--- |
| **CT01** | Visualização do Catálogo | Acesse a página inicial da loja. | Exibir o grid de produtos com nome, imagem, preço e tamanho. | **Passou (Aprovado)** |
| **CT02** | Filtro por Categoria | Selecione o filtro "Camisetas" ou "Moletons". | Exibir apenas as peças pertencentes à categoria selecionada. | **Passou (Aprovado)** |
| **CT03** | Busca de Produtos | Digite o nome de uma peça no campo de pesquisa. | Filtrar em tempo real as peças correspondentes à pesquisa. | **Passou (Aprovado)** |
| **CT04** | Adição ao Carrinho | Selecione o tamanho e clique em "Adicionar ao Carrinho". | Atualizar o badge e abrir o gaveteiro do carrinho com o item. | **Passou (Aprovado)** |
| **CT05** | Validação de Limite de Estoque | Tente adicionar quantidade maior que o saldo em estoque. | Exibir alerta de limite e bloquear adição superior ao disponível (RN01). | **Passou (Aprovado)** |
| **CT06** | Remoção e Subtotal | Altere a quantidade ou remova um item do carrinho. | Recalcular automaticamente o valor total do pedido (RN03). | **Passou (Aprovado)** |
| **CT07** | Simulação de Checkout | Finalize a compra preenchendo os dados de simulação. | Registrar o pedido e aplicar a baixa automática no estoque (RN02). | **Passou (Aprovado)** |
| **CT08** | Autenticação do Admin | Efetue login na área administrativa com credenciais válidas. | Permitir acesso ao Painel Admin e liberar ações de CRUD. | **Passou (Aprovado)** |
| **CT09** | Gestão de Estoque e Produtos | Altere a quantidade de estoque de uma peça no Painel Admin. | Salvar a alteração no Vercel Postgres e refletir na loja. | **Passou (Aprovado)** |

---

### 3. Testes de Segurança e Erros

| ID | Tipo de Teste | Descrição / Tentativa | Resultado Obtido | Status |
| :--- | :--- | :--- | :--- | :--- |
| **TS01** | Proteção de Rotas | Acesso direto via URL à rota `/admin` sem efetuar login. | Redirecionamento automático para a tela de Login. | **Passou (Aprovado)** |
| **TS02** | Tratamento de Erro | Busca por produto inexistente ou ID inválido na URL. | Exibição de tela amigável (Página 404 / Sem resultados). | **Passou (Aprovado)** |

---

## PARTE 2: TERMO E RELATÓRIO DE HOMOLOGAÇÃO DE CLIENTE

### 1. Informações da Homologação
- **Ambiente de Homologação:** Vercel (Produção/Preview Online)
- **Status da Validação:** Aprovado para Produção
- **Responsável pela Validação:** Luiz (Cliente / Responsável do Projeto)

### 2. Checklist de Validação Final
- [x] Interface e Identidade Visual (Cyber Y2K / Dark Streetwear) conforme protótipo no Figma.
- [x] Vitrine e catálogo de produtos operando sem lentidão.
- [x] Regras de negócio de estoque (trava e baixa automática) validadas.
- [x] Carrinho de compras calculando os valores corretamente.
- [x] Painel administrativo permitindo gerenciamento do catálogo.
- [x] Aplicação responsiva em dispositivos móveis e desktops.

### 3. Parecer de Aceite
A aplicação **CYBER CULT** foi testada e homologada com sucesso no ambiente online. Todos os casos de teste planejados foram executados com status de aprovação, confirmando que o sistema atende integralmente aos Requisitos Funcionais (RF) e Regras de Negócio (RN) estabelecidos nas etapas anteriores.
