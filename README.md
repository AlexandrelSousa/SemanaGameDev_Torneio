# Tournament Team Balancer — README

**Projeto:** Balanceador de Times — Torneio Semana GameDev

**Descrição rápida**
Uma página web (HTML/CSS/JS) com tema *glitch / cyberpunk* que ajuda organizadores de torneios a verificar se um time está balanceado para competir. O usuário seleciona a modalidade (Valorant, Free Fire, Wild Rift), informa os elos dos membros do time e o sistema calcula uma pontuação/peso e indica se o time está:

* **Na medida certa** — apto para competir;
* **Forte demais** — risco de desequilíbrio no torneio;

## Estrutura do projeto

```
/tournament-team-balancer/
├─ tournament-team-balancer.html    # arquivo principal (HTML/CSS/JS embutido)
├─ virus.png                        # placeholder de logo (troque pela sua)
├─ README.md                        # este arquivo
```

> Observação: todo o código está embarcado no único arquivo HTML para facilitar testes e deploy estático.

---

## Como funciona a lógica de balanceamento

* Cada elo tem um **peso numérico** (definido no arquivo JS) por modalidade.
* O sistema calcula a **soma** dos pesos do time e a **média por jogador**.
* Compara a média com uma **faixa ideal (target ± tolerância)** para decidir o estado do time.

### Pesos padrão (atual)

* **Valorant:** Iron(1) → Radiant(9)
* **Free Fire:** Bronze(1) → Grandmaster(7)
* **Wild Rift:** Iron(1) → Challenger(10)

### Targets e tolerância

* `targets = { freefire:4, valorant:5, wildrift:6 }`
* `tol = 1` (faixa = target ± 1)

> Você pode ajustar `weights`, `targets` e `tol` no topo do `<script>` para calibrar o balanceamento do seu torneio.
