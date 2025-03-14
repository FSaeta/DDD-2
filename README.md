# 📚 Design Estratégico do Projeto

## 📌 Aula 1: Introdução ao Domain-Driven Design (DDD)

### **1️⃣ Revisão da Aula**
- O que é **Domain-Driven Design (DDD)**?
- Diferença entre **Complexidade Essencial vs. Complexidade Acidental**.
- **Subdomínios**: Core Domain, Supporting Subdomains e Generic Subdomains.
- **Bounded Contexts**: Separando conceitos e linguagens dentro do domínio.

### **2️⃣ Identificação dos Subdomínios**
| **Subdomínio**              | **Descrição**                                                                                      | **Tipo**         |
|-----------------------------|--------------------------------------------------------------------------------------------------|------------------|
| Criação de Partidas         | Gerencia a sugestão e seleção de locais próximos para a prática do esporte selecionado.        | Core Domain      |
| Gerenciador de Players da Partida  | Gerencia os players inscritos na partida, definindo sempre uma Modalidade para aplicar as regras. | Core Domain       |
| Gerenciamento de Locais    | Cadastro e validação de Locais de esportes, pelo gerente do local.   | Supporting       |
| Pagamentos    | Processa pagamentos e status de pagamento dos players inscritos nas partidas.  | Generic   |
| Feed de Partidas  | Mostra partidas dos esportes preferídos dos usuários, nas proximidades do usuário ou localização definida. | Generic |
| Autenticação de Usuários    | Gerencia login, permissões e segurança de acesso. | Generic |

---

## 📌 Aula 2: Mapeamento de Contextos (Context Mapping)

### **1️⃣ Objetivo da Aula**
Nesta aula, vamos:
✅ Explorar como **Bounded Contexts** se relacionam entre si.  
✅ Aplicar **Context Mapping** para visualizar dependências entre contextos.  
✅ Criar um **diagrama de Context Mapping** para um projeto.  

---

### **2️⃣ Atividade Prática: Context Mapping no Projeto**

📌 **Objetivo:**  
Identifique os **Bounded Contexts** do projeto e criar um **Context Map**, definindo as relações entre eles.

📌 **Instruções:**  
1️⃣ **Escolha um projeto** (real ou fictício). Ou utilize o seu projeto da aula 1. Pode ser um e-commerce, um sistema de saúde, um banco digital. 
2️⃣ **Liste os Bounded Contexts** que fazem parte do sistema.  
3️⃣ **Defina os relacionamentos** entre os contextos usando os padrões do Context Mapping (**Customer-Supplier, Shared Kernel, Anticorruption Layer, etc.**).  
4️⃣ **Crie um diagrama** representando o Context Map.  
5️⃣ **Justifique suas escolhas** (por que cada relacionamento foi modelado dessa forma?).  

📌 **Exemplo de Resposta para o Keller’s Health:**  

| **Origem**               | **Destino**              | **Tipo de Relacionamento**       | **Explicação** |
|--------------------------|-------------------------|--------------------------------|---------------|
| Contexto de Consultas    | Contexto de Pagamentos  | **Customer-Supplier**          | O pagamento depende do status da consulta. |
| Contexto de Cadastro     | Contexto de Consultas   | **Shared Kernel**              | Pacientes e médicos são compartilhados entre os dois contextos. |
| Contexto de Comunicação  | Contexto de Consultas   | **Conformist**                 | O contexto de comunicação apenas consome dados da consulta para iniciar uma chamada de vídeo. |
| Contexto de Pagamentos   | Contexto de Consultas   | **Anticorruption Layer (ACL)** | O sistema de consultas traduz dados financeiros sem impactar seu modelo de domínio. |

📌 **Formato de Entrega:**  
- O trabalho pode ser entregue em **Markdown (.md), PDF ou apresentação (PPT)**.  
- O diagrama pode ser anexado como **imagem** ou **link para uma ferramenta online**.  
- Entrega via **repositório Git** ou outra plataforma definida pelo professor.  

📌 **Ferramentas para Criar o Diagrama:**  
- [Miro](https://miro.com/)  
- [Lucidchart](https://www.lucidchart.com/)  
- [Figma](https://www.figma.com/)  

## 📌 Aula 3: Próximos Passos  
Na próxima aula, vamos explorar **Design Tático**, abordando:  
🔹 **Entidades vs. Value Objects** – Como diferenciar e modelar corretamente.  
🔹 **Agregados** – Como definir o agregado raiz e garantir consistência.  
🔹 **Repositórios** – Como separar persistência da lógica de domínio.  

📌 **Prepare-se!** Tente aplicar **Context Mapping** no seu projeto antes da próxima aula.  

---

**📢 Bom trabalho! Nos vemos na próxima aula! 🚀**  
