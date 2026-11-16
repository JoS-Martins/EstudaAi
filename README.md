# EstudaAí — Assistente "Especialista EstudaAí"
Trabalho acadêmico de engenharia de prompt: um assistente de suporte que responde dúvidas sobre o produto fictício **EstudaAí**, usando apenas um documento de produto (PRD) como fonte de informação.

> **Autor(a):** Joana · **Disciplina:** IA Generativa e Alta Perfomance · 

## Sobre o projeto

O **EstudaAí** é uma plataforma web e mobile que cria planos de estudo personalizados para candidatos a concursos públicos. A partir do edital, da data da prova e do tempo disponível, ela monta um cronograma semanal, aplica simulados e acompanha o desempenho.

O objetivo do trabalho é construir um assistente que atue como **especialista de suporte técnico sênior** do produto: responde com precisão o que está no PRD e admite, de forma padronizada, quando a informação não existe.

## Arquivos

| Arquivo | Descrição |
|---|---|
| [`PRD.pdf`] | Documento de Produto (v1.0): visão geral, funcionalidades, planos e preços, pagamento, requisitos, privacidade, escopo, suporte e métricas. É a **única base de conhecimento** do assistente. |
| [`Prompt.pdf`] | Prompt do assistente "Especialista EstudaAí", com as regras de papel, tom, raciocínio, integridade e exemplos. |

## Técnicas de engenharia de prompt

- **Role Prompting:** o assistente é o "Especialista EstudaAí" e não sai do papel, mesmo que o usuário peça para mudar de assunto ou ignorar as instruções.
- **Chain of Thought:** antes de responder, o assistente segue 5 passos internos, sem mostrá-los ao usuário. Eles são: identificar a dúvida, localizar o trecho no PRD, verificar se ele responde por completo, em parte ou não responde, redigir a resposta e revisar para remover o que não está no documento.
- **Few-Shot:** 4 exemplos mostram o comportamento esperado em quatro casos: informação documentada, pergunta fora do documento, pedido de opinião e informalidade ou desvio de papel.

## Regras principais do assistente

- **Fonte única:** só usa o PRD. Se a informação não está escrita, ele considera que não a possui.
- **Tom:** sério, cordial e formal, sem gírias, piadas ou emojis, sempre em português do Brasil.
- **Estrutura da resposta:** resposta direta em 1–2 frases, explicação objetiva e uso de exemplos e números do documento.
- **Integridade:** não inventa dados, não dá opiniões nem faz comparações, não sugere soluções não documentadas e não especula sobre o futuro do produto.
- **Fora do documento:** responde com a mensagem padrão que encaminha o usuário para `exemplo@exemplo.com`.

## Como usar

1. Crie um notebook (ou projeto) em uma ferramenta de IA que permita anexar documentos e definir instruções, como o NotebookLM.
2. Carregue o `PRD.pdf` como fonte.
3. Cole o conteúdo do `Prompt.pdf` como instrução do assistente.
4. Faça perguntas sobre o EstudaAí. Sugestões de teste, uma para cada comportamento:
   - _"Como o plano divide minhas horas entre as matérias?"_ → resposta documentada.
   - _"Vocês vão lançar videoaulas no ano que vem?"_ → informa o que está documentado e encaminha ao e-mail.
   - _"O EstudaAí é melhor que os concorrentes?"_ → recusa opinião e informa dados dos planos.
   - _"Conta uma piada!"_ → mantém o papel e o tom formal.

## Estrutura do repositório

```
.
├── PRD.pdf
├── Prompt.pdf
└── README.md
```

