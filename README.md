Documento de Engenharia de Prompt 

Este documento descreve a arquitetura de prompts utilizada no agente LLM implementado no notebook.
O fluxo é baseado em um seletor de funcionalidades (1 a 4) e, para cada funcionalidade, o comportamento do modelo é controlado principalmente pelo System Prompt, seguido pelo User Prompt inserido em tempo real.



Funcionalidade F1 — Levantamento da Situação Profissional Atual
🟦 Objetivo:

Coletar informações sobre o trabalho atual do usuário e suas atividades diárias.

🔹 System Prompt (F1)

“Solicite que o usuário descreva qual é o seu trabalho atual e liste as principais atividades que realiza no dia a dia.”

🔹 User Prompt (F1)

Entrada livre do usuário, exemplo típico:

"Sou analista de suporte, mas quero migrar para outra área. Meu dia é basicamente atendimento ao usuário."

🔹 Estratégia Utilizada

O system prompt define um comportamento entrevistador e conduz o usuário a fornecer detalhes profissionais.

Não há formatação exigida nem estrutura rígida.
<img width="1793" height="566" alt="Image" src="https://github.com/user-attachments/assets/8b786a88-b5b9-4bad-ab70-d923b28380cb" />



Funcionalidade F2 — Mapeamento de Habilidades Transferíveis
🟦 Objetivo:

Com base na profissão relatada, a IA identifica habilidades técnicas e comportamentais que podem ser aproveitadas em outras áreas da tecnologia.

🔹 System Prompt (F2)

“Considerando a profissão informada e as habilidades mencionadas, identifique as competências técnicas e comportamentais transferíveis. Explique como essas competências podem auxiliar o usuário a evoluir de forma estruturada e eficaz.”

🔹 User Prompt (F2)

Utiliza a descrição dada na F1, por exemplo:

“Sou desenvolvedor front-end e trabalho com React.”

🔹 Estratégia Utilizada

O system prompt orienta a IA a atuar como analista de carreira.

Extração de habilidades implícitas e explícitas.
<img width="1793" height="566" alt="Image" src="https://github.com/user-attachments/assets/97ce89ec-0dbe-4eaf-96a8-1980a4dd83c6" />



Funcionalidade F3 — Recomendação de Reskilling
🟦 Objetivo:

Gerar um plano objetivo para que o usuário se recoloque no mercado, sugerindo novas habilidades.

🔹 System Prompt (F3)

“Elabore uma recomendação completa de reskilling para o usuário, considerando tendências atuais e demandas emergentes no mercado de trabalho. Sugira de 3 a 5 habilidades novas que ele deveria desenvolver para ampliar suas chances de recolocação.”

🔹 User Prompt (F3)

Entra quando o usuário pede orientação, exemplo:

“Quero migrar para segurança da informação.”

🔹 Estratégia Utilizada

Focado em mercado atual + tendências.

Recomendações práticas e imediatas.

Oferece direcionamento de estudo.



Funcionalidade F4 — Simulação de Entrevista
🟦 Objetivo:

Realizar uma entrevista profissional com três perguntas adequadas ao perfil informado.

🔹 System Prompt (F4)

“Conduza uma breve entrevista com o usuário composta por três perguntas objetivas, projetadas para revelar sua experiência, capacidades e expectativas profissionais.”

🔹 User Prompt (F4)

O usuário interage como em um diálogo normal, por exemplo:

“Podemos começar.”

🔹 Estratégia Utilizada

System prompt define um comportamento estruturado, formato entrevista.

A IA responde com perguntas, não com respostas completas.



 Considerações Finais

O sistema utiliza apenas System + User prompts, sem exemplos adicionais.

As funcionalidades são moduladas por condicionais no código (if usuario == N).

A temperatura baixa aumenta consistência.

O modelo usado (gpt-4o-mini) é suficiente para respostas rápidas e objetivas.
