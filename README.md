# Go - Saga and-others

Projeto em Go com exemplos de padrões (saga), arquitetura interna (`cmd` / `internal`), e adaptadores.

Visão geral

- Estrutura: `cmd/` (entradas/CLI), `internal/` (domínio, portas, adaptadores), `saga-pattern/` (exemplo didático).
- Contém exemplos didáticos de orquestração (saga) e processamento de eventos/market feed.

Como rodar exemplos rápidos

- Requisitos: Go 1.20+ instalado.
- Rodar o exemplo raiz (quando existir `main`):
  ```powershell
  cd E:\Dev\go-lang
  go run init.go
  ```
- Rodar o exemplo de boas práticas:
  ```powershell
  go run examples\go_best_practices_example.go
  ```

Boas práticas resumidas (Go)

- **Módulo:** use `go mod init` e mantenha `go.mod` com versões explícitas.
- **Formatar:** execute `gofmt` / `goimports` automaticamente. Ex.: `gofmt -w .`.
- **Lint:** adote `golangci-lint` com um `/.golangci.yml` na raiz.
- **Vet:** rode `go vet ./...` regularmente.
- **Testes:** escreva testes unitários com `testing` e use `httptest` para handlers HTTP.
- **Context:** aceite `context.Context` em funções que fazem IO/long-running para cancelamento e deadlines.
- **Erros:** empacote erros com `%w` (`fmt.Errorf("...: %w", err)`) para wrap e inspeção com `errors.Is`/`errors.As`.
- **Interfaces pequenas:** defina interfaces no consumidor (dependente), não no implementador.
- **Injeção de dependência:** use construtores que recebam interfaces para facilitar testes.
- **Logging:** prefira loggers estruturados (`zap`, `logrus`) em vez de `fmt.Println` no código de produção.
- **Concorrência:** escolha canais ou `sync` primitives conscientemente; use `-race` para detectar data races.
- **Perf/Profiling:** utilize `pprof` quando necessário para investigar hotspots.
- **CI:** inclua checks (`gofmt`, `go vet`, `golangci-lint`, `go test`) na pipeline.

Arquivos úteis

- Saga de exemplo: `saga-pattern/init.go`
- Entradas: `projeto-broker/cmd/*`
- Domínio e portas: `projeto-broker/internal/domain`, `projeto-broker/internal/ports`

Exemplo de código com boas práticas está em `examples/go_best_practices_example.go`.

Próximos passos sugeridos

- Adicionar `/.golangci.yml` e pipeline CI (GitHub Actions / Azure Pipelines).
- Adicionar testes para `saga-pattern` e para adaptadores do `projeto-broker`.

Contribuições

- Sinta-se à vontade para abrir issues e PRs com melhorias, exemplos adicionais e templates de CI.

---

Feito automaticamente: README com instruções básicas e boas práticas em Go.
