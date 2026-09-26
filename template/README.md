# Template de Curso — Aprendizado com Hermes

Estrutura padrão para qualquer curso novo. O agente Hermes (tutor) usa estes arquivos
como fonte de verdade; o Discord é a sala de aula; o cron entrega as aulas.

## Estrutura

```
<nome-do-curso>/
├── curso.json          # metadados: título, nº de aulas, horário de entrega, canais Discord
├── progresso.json      # estado do aluno: aula atual, checklists, notas (ATUALIZADO PELO TUTOR)
├── aulas/
│   ├── 01.md           # uma aula por arquivo: explicação + exemplos + exercícios
│   └── ...
└── exercicios/         # gabaritos separados (o aluno não deve olhar antes de responder)
```

## Regras do tutor

1. **Entrega diária**: cron envia a aula do dia no canal #anuncios às HH:MM.
2. **Correção adaptativa**: o aluno responde no #exercicios; o tutor corrige, explica
   erros e ajusta profundidade. Registros de desempenho vão para progresso.json.
3. **Gate de domínio**: a semana só avança quando todos os itens do checklist da
   semana estiverem `true`. O checklist é marcado após o teste de domínio.
4. **Testes de domínio**: nas aulas de consolidação, o tutor gera 5 questões novas
   (nunca repetidas) e registra a nota.
5. **Revisão espaçada**: cada aula começa com 1–2 perguntas de recuperação da
   semana anterior.
6. **Versionamento**: cada semana concluída = entrada no CHANGELOG + tag.

## Criando um curso novo

1. Copie esta pasta `template/` para `<nome-do-curso>/`
2. Escreva `aulas/*.md` (o Hermes pode gerar a partir de qualquer material: PDF, livro, artigo)
3. Preencha `curso.json` (canais do Discord + horário do cron)
4. Crie a categoria no Discord e aponte os IDs dos canais
5. Configure o cron de entrega
