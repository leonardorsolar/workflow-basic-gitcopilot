# Workflow básico com GitHub Copilot (Agent)

Este repositório define um processo simples para transformar uma ideia de produto em documentação de execução de tarefa, usando prompts guiados no Copilot.

## Objetivo

Padronizar como o time cria e mantém:
- PRD Geral do produto
- PRD por tarefa
- TechSpec por tarefa
- Plano de implementação por tarefa

## Estrutura atual

- `docs/tutorial.md`: tutorial do fluxo completo (PRD Geral → PRD Tarefa → TechSpec → Plano → Implementação), além de sugestões de rules e skills.
- `prompts/pdr_geral.md`: prompt para conduzir perguntas e gerar o PRD Geral.
- `prompts/prd_tarefa.md`: prompt para conduzir perguntas e gerar o PRD da tarefa com base no PRD Geral.
- `prompts/techspec_tarefa.md`: prompt para conduzir perguntas técnicas e gerar a TechSpec da tarefa.

## Fluxo recomendado para devs

1. **Gerar PRD Geral**
   - Usar o prompt de `prompts/pdr_geral.md`.
   - Saída esperada: `docs/PRD_GERAL.md`.

2. **Gerar PRD da tarefa**
   - Usar o prompt de `prompts/prd_tarefa.md`.
   - O prompt considera `docs/PRD_GERAL.md` como contexto.
   - Saída esperada: `docs/tarefas/tarefa-00X/PRD_TAREFA_00X.md`.

3. **Gerar TechSpec da tarefa**
   - Usar o prompt de `prompts/techspec_tarefa.md`.
   - O prompt considera o PRD Geral e o PRD da tarefa.
   - Saída esperada: `docs/tarefas/tarefa-00X/TECHSPEC_TAREFA_00X.md`.

4. **Gerar plano de execução**
   - Com base no PRD da tarefa + TechSpec.
   - Saída sugerida: `docs/tarefas/tarefa-00X/PLANO_TAREFA_00X.md`.

5. **Executar a skill**
   - Validar com a skill desejada

## Resultado esperado do processo

Ao final de cada tarefa, o time deve ter:
- PRD da tarefa claro
- TechSpec objetiva (incluindo contrato de interface quando aplicável)
- Plano de implementação executável
- Implementação alinhada ao que foi especificado

---

Se for a primeira vez no projeto, comece por `docs/tutorial.md` e siga a sequência dos prompts na pasta `prompts/`.

Resumidamente:

## Crie o PRD Geral  
#pdr_geral.md
## Crie o PRD da tarefa
#pdr_tarefa.md
## Crie o techspec da tarefa
#techspec_tarefa.md
## Crie o plano da tarefa
crie um plano para a tarefa001 e leia os arquivos #PRD_TAREFA_001.md #TECHSPEC_TAREFA_001.md
## 5- Implementação
 Impemente o plano salvando os arquivos na raiz do projeto
## 6- Adiconar rules ao projeto
## 7- Adiconar skills
## 8- Adiconar mcp server