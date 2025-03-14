# Entrega da Atividade DDD-2

### Alunos:

| Nome                           | RM      |
|--------------------------------|--------|
| FERNANDO REBELATO SAETA       | 359961 |
| INGO HENRIQUE ALMENDROS GIRÃO | 358616 |
| KALEO VIEIRA LEITE            | 359754 |
| NATHAN GRECCO FONSECA         | 359289 |

## 1. Escolha do Projeto:
**Mesmo da Aula 1:**

> **Game Now**: Conectar jogadores de níveis compatíveis a partidas esportivas coletivas, simplificando a organização e facilitando o acesso a locais acessíveis.

## 2. Liste os Bounded Contexts que fazem parte do sistema:

| **Bounded Context**           | **Responsabilidade**                                                              | **Subdomínios Relacionados** |
|-------------------------------|-----------------------------------------------------------------------------------|------------------------------|
|Agendamento de Partidas| Criação de eventos, gestão de horários, notificação de participantes e integração com locais. | Agendamento de Partidas, Sistema de Localização|
|Gerenciamento de Times| Formação de equipes, convites a jogadores e participação em competições.| Gerenciamento de Times, Avaliação de Habilidades, Players |
Localização |Integração com APIs de mapas e filtragem de espaços com base em acessibilidade e avaliações|Sistema de Localização |
| Locais de Esporte | Armazena informações sobre os locais, reputação, localização relacionadas com as modalidades de esportes. | Modalidade de Esportes, Agendamento de Partidas, Localização |
Players | Armazena dados de nível técnico, histórico de partidas e reputação.|Avaliação de Habilidades|
| Esportes | Manter preferências dos players e criação de regras para cada Modalidade. | Agendamento de Partidas, Organização de Players da Partida, Modalidade de Esportes |

## 3. Defina os relacionamentos entre os contextos usando os padrões do Context Mapping (Customer-Supplier, Shared Kernel, Anticorruption Layer, etc.):

| **Origem**                  | **Destino**                | **Tipo de Relacionamento**       | **Explicação** |
|-----------------------------|---------------------------|----------------------------------|---------------|
| Agendamento de Partidas     | Players         | **Shared Kernel**           | O agendamento de partidas possui um dono relacionado, e o dono da partida e seus integrantes conseguem visualizar a mesma em "Minhas Partidas". |
| Agendamento de Partidas     | Gerenciamento de Times    | **Customer-Supplier**           | O agendamento cria estrutura para formação de times com os jogadores inscritos. |
| Agendamento de Partidas     | Locais de Esporte         | **Customer-Supplier**           | A disponibilidade dos locais influencia diretamente a criação das partidas. |
| Agendamento de Partidas     | Esportes                  | **Anticorruption Layer (ACL)**   | As partidas podem consumir os esportes disponíveis sem alterá-los. |
| Gerenciamento de Times      | Agendamento de Partidas   | **Conformist**                  | O gerenciamento de times apenas informa o agendamento quando uma equipe é formada. |
| Gerenciamento de Times      | Players                   | **Shared Kernel**           | O gerenciamento de times depende das informações dos jogadores para definir os times e os players conseguem ver informações de seus times. |
| Gerenciamento de Times      | Avaliação de Habilidades  | **Customer-Supplier**           | O desempenho dos jogadores nas partidas impacta diretamente sua avaliação de habilidades. |
| Localização                   | Agendamento de Partidas   | **Customer-Supplier**           | O agendamento de partidas precisa das informações de localização para sugerir locais adequados. |
| Localização                 | Locais de Esporte         | **Shared Kernel**               | Ambos compartilham dados sobre a geolocalização e acessibilidade dos locais. |
| Locais de Esporte           | Agendamento de Partidas   | **Shared Kernel**  | O sistema de partidas consulta dados dos locais, e indisponibiliza o local caso confirmação da Partida. |
| Players                     | Avaliação de Habilidades  | **Customer-Supplier**           | A avaliação depende do desempenho dos jogadores em partidas passadas. |
| Players                     | Esportes                  | **Conformist**                  | O sistema de esportes apenas consome as preferências dos jogadores sem influenciar sua estrutura. |


## 4. Crie um diagrama representando o Context Map:
![Context Map](/DDD-2/context-map.png)

## 5. Justifique suas escolhas:
- **Agendamento de Partidas -> Players** (Shared Kernel): O agendamento de partidas possui um dono relacionado, e o dono da partida e seus integrantes conseguem visualizar a mesma em "Minhas Partidas".
- **Agendamento de Partidas -> Gerenciamento de Times** (Customer-Supplier): O agendamento cria estrutura para formação de times com os jogadores inscritos.
- **Agendamento de Partidas -> Locais de Esporte** (Customer-Supplier): A disponibilidade dos locais influencia diretamente a criação das partidas.
- **Agendamento de Partidas -> Esportes** (Anticorruption Layer (ACL)): As partidas podem consumir os esportes disponíveis sem alterá-los.
- **Gerenciamento de Times -> Agendamento de Partidas** (Conformist): O gerenciamento de times apenas informa o agendamento quando uma equipe é formada.
- **Gerenciamento de Times -> Players** (Shared Kernel): O gerenciamento de times depende das informações dos jogadores para definir os times e os players conseguem ver informações de seus times.
- **Gerenciamento de Times -> Avaliação de Habilidades** (Customer-Supplier): O desempenho dos jogadores nas partidas impacta diretamente sua avaliação de habilidades.
- **Localização -> Agendamento de Partidas** (Customer-Supplier): O agendamento de partidas precisa das informações de localização para sugerir locais adequados.
- **Localização -> Locais de Esporte** (Shared Kernel): Ambos compartilham dados sobre a geolocalização e acessibilidade dos locais.
- **Locais de Esporte -> Agendamento de Partidas** (Shared Kernel): O sistema de partidas consulta dados dos locais e indisponibiliza o local caso confirmação da Partida.
- **Players -> Avaliação de Habilidades** (Customer-Supplier): A avaliação depende do desempenho dos jogadores em partidas passadas.
- **Players -> Esportes** (Conformist): O sistema de esportes apenas consome as preferências dos jogadores sem influenciar sua estrutura.



