# Formato das Instruções

A forma como as instruções são formatadas pode afetar a forma como o modelo de IA interpreta o prompt. Isso é conhecido como **viés de proximidade**, onde as informações localizadas no final do prompt podem ter mais influência sobre a saída do que as informações no início.

Por exemplo, se você estiver usando um modelo de chat, as mensagens mais recentes na conversa incluída no prompt terão um impacto maior sobre a resposta. Portanto, colocar informações importantes mais próximas do final do prompt pode resultar em uma resposta melhor.

## Usando Marcadores de Seção

Uma técnica específica para formatar instruções é dividir as instruções no início ou no final do prompt e deixar o conteúdo do usuário em blocos `---` ou `###`. Essas marcas permitem que o modelo diferencie mais claramente entre instruções e conteúdo.

```markdown
Translate the text into French

---
What's the weather going to be like today?
---
```

## Conteúdo Primário, de Suporte e de Base

Incluir conteúdo para o modelo usar nas respostas permite que ele responda com maior precisão. Esse conteúdo pode ser visto de duas maneiras: conteúdo primário e de suporte.

O conteúdo principal diz respeito ao conteúdo que é o tema da consulta, como uma frase a ser traduzida ou um artigo a ser resumido. Muitas vezes, esse conteúdo é incluído no início ou no final do prompt (como uma instrução e diferenciado por blocos `---`), com instruções explicando o que fazer com ele.

```markdown
---
<insert full article here, as primary content>
---

Summarize this article and identify three takeaways in a bulleted list
```

O conteúdo de suporte pode alterar a resposta, mas não é o foco ou assunto do prompt. Exemplos de conteúdo de suporte incluem itens como nomes, preferências, data futura a ser incluída na resposta e assim por diante. Fornecer conteúdo de suporte permite que o modelo responda de maneira mais completa e precisa e tenha maior probabilidade de incluir as informações desejadas.

```markdown
---
<insert full email here, as primary content>
---
<the next line is the supporting content>
Topics I'm very interested in: AI, webinar dates, submission deadlines

Extract the key points from the above email, and put them in a bulleted list:
```

O conteúdo de base permite que o modelo forneça respostas confiáveis fornecendo conteúdo do qual o modelo pode extrair a resposta. O conteúdo de base pode ser uma redação ou um artigo sobre o qual você faz perguntas, um documento de perguntas frequentes da empresa ou informações mais recentes do que os dados nos quais o modelo foi treinado. Se você precisa de respostas mais confiáveis e atuais ou precisar fazer referência a informações não publicadas ou específicas, o conteúdo de base é altamente recomendado.

```markdown
---
<insert unpublished paper on the history of AI here, as grounding content>
---

Where and when did the field of AI start?
```

## Pistas

Pistas são palavras indicativas em que o modelo se baseia e, muitas vezes, ajudam a levar a resposta para a direção certa. Elas geralmente são usadas com instruções, mas nem sempre. As pistas são particularmente úteis ao solicitar do modelo uma geração de código.

```markdown
Write a join query to get customer names with purchases in the past 30 days between tables named orders and customer on customer ID. 

SELECT
```

Outro exemplo, dada uma grande coleção de resenhas de clientes em um prompt e terminando com:

```markdown
Summarize the reviews above:
Most common complaints:
- 
```

Em seguida, o modelo sabe completar as afirmações com base no contexto fornecido nas resenhas.
