# 🌡️ Queridômetro – Google Classroom

Uma aplicação web simples de avaliação de sentimentos (estilo "Termômetro") projetada para acompanhar o engajamento e as percepções dos alunos ao longo de um curso sobre o Google Classroom no SENAI.

## 🎯 Objetivo

Permitir que o professor avalie diariamente o "clima" da turma. A cada dia, os alunos respondem a uma pergunta rápida sobre como estão se sentindo em relação aos conteúdos apresentados. O site calcula o humor médio e exibe visualmente em um termômetro iterativo, junto com a opção líder.

## ✨ Funcionalidades

- **Múltiplos Dias (Abas):** 4 dias de avaliação pré-configurados.
- **Sistema de Travas (Locks):** O professor controla quais dias estão visíveis/liberados para a turma.
- **Termômetro Animado:** Um termômetro interativo em SVG que muda de cor (de vermelho a verde) dependendo da média dos votos (Humor Médio).
- **Estatísticas em Tempo Real:** Exibição da porcentagem e quantidade de votos local.
- **Sem Dependência de Backend:** A aplicação roda 100% no navegador (Vanilla JS, CSS e HTML).

## ⚙️ Como Configurar e Utilizar

Por ser uma aplicação totalmente estática (ideal para rodar no Google Sites ou GitHub Pages), o estado de liberação e os resultados globais são controlados pela edição direta no código-fonte do `index.html`.

### 1. Liberando um dia
Para desbloquear o questionário de um novo dia para os alunos, edite a constante `LOCKS` no código:
```javascript
const LOCKS = {
  d1: true,  // Liberado
  d2: true,  // Liberado
  d3: false, // Bloqueado
  d4: false  // Bloqueado
};
```
Após alterar, basta salvar/publicar o arquivo novamente.

### 2. Atualizando Resultados Globais
Como não há um banco de dados integrado, os votos confirmados em sala (via Forms ou contagem manual) podem ser alimentados no sistema agregando-os na constante `RESULTS`:
```javascript
const RESULTS = {
  d1: [8, 5, 2, 1, 0], // Quantidade de votos para as opções 1 a 5 do Dia 1
  d2: [0, 0, 0, 0, 0],
  // ...
};
```
Isso atualizará os gráficos, as porcentagens de resposta e o nível visual do Termômetro.

## 🚀 Tecnologias

- **HTML5** e **CSS3** puros (utilizando variáveis, Grid, Flexbox e animações CSS).
- **JavaScript Vanilla** (ECMAScript 6+).
- Ícones em formato de Emojis e ilustrações em SVG.
