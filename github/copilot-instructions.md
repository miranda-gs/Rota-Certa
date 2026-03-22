---
description: "Instruções do Copilot para este repositório: foco em backend Java Spring e frontend, contexto de Rota-Certa."
---

# Copilot Instructions (Rota-Certa)

Estas instruções ajudam o GitHub Copilot a entender seu fluxo de trabalho no projeto.

## Uso geral

- Projetos principais:
  - backend: Java + Spring Boot
  - frontend: (framework no diretório frontend)
- Evitar mudanças que quebrem a estrutura do pacote em `backend/src/main/java/com/miranda_gs/rotacerta`.

## Coisas que o Copilot deve priorizar

1. Padrões do Spring Boot (controllers, services, repositories, DTOs)
2. Boas práticas de REST API: status HTTP corretos, validação e tratamento de erros em `exception`.
3. `application.yaml` para configuração compartilhada.
4. Testes unitários em `backend/src/test/java` com JUnit/Mockito.

## Estilo de código

- Nomes em inglês para classes e métodos públicos.
- Comentários em português apenas quando o conceito é específico ao domínio do cliente (Rota-Certa).
- Use `var` com estilo local apenas em código Java 10+.

## Gatilhos e prompts úteis

- "corrija o erro de validação" → foco em `@Valid`, `BindingResult` e `@ExceptionHandler`
- "otimize consulta do repositório" → foco em JPA `@Query` e índices
- "adicione endpoint" → foco em `@RestController`, `@GetMapping`, `@PostMapping`

## Restrição

- Não sugira dependências de bibliotecas grandes sem aprovar.
- Para novas features, comente se precisar de mudanças de DB e injeções de dependência.
