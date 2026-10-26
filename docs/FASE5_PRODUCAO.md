# 🚀 Documento de Implantação em Produção e Gestão de Backups (Fase 5)

> 📥 **Download da Versão Oficial:** [Clique aqui para baixar o PDF completo da Fase 5](Documento_Fase5_Producao_e_Deploy.pdf)  
> 🌐 **Sistema Publicado (Produção):** [Acessar Loja Cyber Y2K Live](https://criar-loja-online-via-figma-e8oqosras.vercel.app)

---

**Projeto:** Sistema de Gerenciamento e Vendas para Loja de Roupas (Cyber Y2K / Dark Streetwear)  
**Responsável:** Luiz  

---

## 1. Configuração do Servidor de Produção
A implantação definitiva do sistema **CYBER CULT** foi realizada na infraestrutura serverless global da Vercel, vinculada diretamente ao repositório do projeto no GitHub.

- **Ambiente:** Produção (Production / Main Branch)
- **Plataforma de Hospedagem:** Vercel Global Edge Network
- **Protocolo de Segurança:** HTTPS com Certificado SSL/TLS Automatizado
- **Domínio de Produção:** [https://criar-loja-online-via-figma-e8oqosras.vercel.app]([https://seu-site.vercel.app](https://criar-loja-online-via-figma-e8oqosras.vercel.app))

---

## 2. Migração e Povoamento Inicial de Dados (Seed Data)
Para disponibilizar o sistema em produção com dados reais prontos para operação, foi executada a rotina de migração e povoamento (*seed script*) no banco de dados **Vercel Postgres**:

- **Estrutura das Tabelas:** Execução dos scripts DDL para criação do esquema final do banco de dados (tabelas `users`, `products`, `product_variants`, `orders` e `order_items`).
- **Catálogo Inicial (Produção):** Inserção do catálogo oficial de roupas no estilo Cyber Y2K / Dark Streetwear com imagens hospedadas e variações de estoque ativas.
- **Usuário Administrador:** Criação da conta de acesso master para o painel administrativo.

---

## 3. Política e Scripts de Backup do Banco de Dados
Para garantir a integridade e disponibilidade contínua dos dados comerciais (catálogo, estoque e histórico de vendas), foram configuradas as seguintes diretivas de backup na infraestrutura Vercel Postgres:

### 3.1 Snapshots Automáticos (Vercel Postgres Native)
- **Frequência:** Diária automatizada pela plataforma da Vercel.
- **Retenção:** Snapshots diários armazenados com histórico contínuo para recuperação rápida em caso de desastre (*Disaster Recovery*).

### 3.2 Script de Dump Manual e Exportação em Nuvem
Além do backup automático gerenciado pela nuvem, foi implementado o script de exportação periódica dos dados via CLI (`pg_dump`) para armazenamento de cópias frias em formato `.sql` / `.csv`.

```bash
# Script de Exportação de Dados em Produção (pg_dump / Vercel CLI)
vercel postgres dump --environment=production > backup_cyber_cult_$(date +%Y%m%d).sql
