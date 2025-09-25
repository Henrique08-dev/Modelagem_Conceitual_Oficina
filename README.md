🛠️ Modelagem Entidade-Relacionamento Estendida (EER) para Oficina Mecânica

Este repositório contém a modelagem completa de um sistema de gestão para oficina mecânica, evoluindo de uma modelagem inicial básica para uma modelagem entidade-relacionamento estendida (EER) refinada e robusta.

📊 Evolução da Modelagem

Modelagem Inicial (`Modelagem Oficina sem refinar.pdf`)
- Modelagem básica com entidades essenciais
- Estrutura inicial com relacionamentos simples
- Ausência de normalização adequada
- Faltavam entidades importantes para operação completa

Modelagem Final Refinada (`Modelagem Oficina Final.pdf`)
- **Modelagem EER completa** com todas as entidades necessárias
- **Normalização** aplicada para evitar redundância
- **Cardinalidades** definidas precisamente
- **Atributos refinados** com tipos de dados apropriados
- **Entidades novas** para operação completa

🏗️ Estrutura da Modelagem Final

Entidades Principais e Seus Atributos

👥 **Cliente**
- `idCliente` INT (PK)
- `Nome` VARCHAR(45)
- `Telefone` VARCHAR(45)
- `Endereco` VARCHAR(45)
- `Email` VARCHAR(45)

🚗 **Veículo**
- `idVeiculo` INT (PK)
- `Modelo` VARCHAR(45)
- `Marca` VARCHAR(45)
- `Ano` INT
- `Placa` VARCHAR(45)
- `kmAtual` INT
- `Cliente_idCliente` INT (FK)

🔧 **Mecânico**
- `idMecanico` INT (PK)
- `Nome` VARCHAR(45)
- `Endereco` VARCHAR(45)
- `Especialidade` VARCHAR(45)
- `Equipe_idEquipe` INT (FK)

👥 **Equipe**
- `idEquipe` INT (PK)
- `nomeEquipe` VARCHAR(45)

📋 **Ordem de Serviço (OS)**
- `idOrdemServico` INT (PK)
- `dataEmissao` DATE
- `valorTotal` FLOAT
- `Status` VARCHAR(45)
- `dataConclusao` DATE
- `Veiculo_idVeiculo` INT (FK)
- `Equipe_idEquipe` INT (FK)

📦 **Peça Catálogo**
- `idPecaCatalogo` INT (PK)
- `Nome` VARCHAR(45)
- `Fabricante` VARCHAR(45)
- `Codigo` VARCHAR(45)
- `valorPadrao` VARCHAR(45)

🔍 **Referência Serviço**
- `idReferenciaServico` INT (PK)
- `descricaoServico` VARCHAR(45)
- `valorMaoDeObra` FLOAT

⏰ **Agendamento** (NOVO)
- `idAgendamento` INT (PK)
- `dataAgendamento` DATE
- `dataCadastroAgendamento` DATE
- `tipoServico` VARCHAR(100)
- `Status` ENUM(...)
- `Observacoes` TEXT
- `Cliente_idCliente` INT (FK)
- `Veiculo_idVeiculo` INT (FK)
- `OrdemServico_idOrdemServico` INT (FK)

💰 **Pagamento**
- `idPagamento` INT (PK)
- `Valor` DECIMAL(10,2)
- `dataPagamento` DATE
- `formaPagamento` ENUM(...)
- `Status` ENUM(...)
- `OrdemServico_idOrdemServico` INT (FK)

🎯 Principais Melhorias Implementadas

1. **Normalização de Dados**
- Eliminação de redundâncias
- Criação de chaves estrangeiras apropriadas
- Separação de conceitos em entidades distintas

2. **Novas Entidades Críticas**
- **Agendamento**: Gerencia marcações de serviços
- **Pagamento**: Controla transações financeiras
- **Histórico de Status**: Rastreia mudanças de status das OS

3. **Refinamento de Tipos de Dados**
- Uso de `ENUM` para campos com valores predefinidos
- `DECIMAL(10,2)` para valores monetários
- `DATETIME` para campos de data/hora
- `TEXT` para observações longas

4. **Cardinalidades Precisas**
- Definição exata das relações entre entidades
- Suporte para relacionamentos opcionais (Agendamento → OS)
- Relacionamentos 1:N e N:1 adequadamente mapeados

5. **Gestão de Estoque e Serviços**
- Catálogo de peças com fabricante e código
- Tabela de referência de serviços com valores de mão de obra
- Controle de quantidade através de tabelas de junção

6. **Rastreabilidade Completa**
- Histórico de status com data/hora e usuário
- Data de criação e conclusão de ordens de serviço
- Controle de agendamentos e pagamentos

📋 Regras de Negócio Implementadas

1. Um cliente pode ter múltiplos veículos
2. Um veículo pertence a um único cliente
3. Uma equipe possui múltiplos mecânicos
4. Uma OS é atendida por uma equipe
5. Um agendamento pode gerar uma OS (relacionamento opcional)
6. Uma OS pode ter múltiplos pagamentos
7. Cada OS contém múltiplos itens de serviço e peças

---

Desenvolvido como parte da Formação Suzano - Análise de Dados com Power BI - Digital Innovation One
