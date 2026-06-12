# 🌡️ Queridômetro – Google Classroom

Uma aplicação web de avaliação de sentimentos (estilo "Termômetro") projetada para acompanhar o engajamento e as percepções dos alunos ao longo de um curso sobre o Google Classroom no SENAI.

## 🎯 Objetivo

Permitir que o professor avalie diariamente o "clima" da turma de forma centralizada. A cada dia, os alunos respondem a uma pergunta rápida sobre como estão se sentindo em relação aos conteúdos apresentados. O site calcula o humor médio em **tempo real** e exibe visualmente em um termômetro animado, junto com a opção líder.

## ✨ Funcionalidades

- **Sincronização em Tempo Real (Firebase):** Quando um aluno vota, o termômetro de todos os outros alunos na sala é atualizado instantaneamente, refletindo a média real da turma sem necessidade de recarregar a página.
- **Múltiplos Dias (Abas):** 4 dias de avaliação pré-configurados.
- **Sistema de Travas (Locks):** O professor controla quais dias estão visíveis/liberados para a turma diretamente no código.
- **Prevenção de Votos Duplos:** Utiliza `localStorage` para impedir que o mesmo aluno vote mais de uma vez na mesma máquina no mesmo dia.
- **Termômetro Animado:** Um termômetro interativo em SVG que muda de cor (de vermelho a verde) dependendo da média dos votos (Humor Médio).

## ⚙️ Como Configurar e Utilizar

A aplicação roda nativamente no front-end (GitHub Pages, Google Sites), enquanto todo o armazenamento de dados é gerenciado automaticamente de forma gratuita pelo **Firebase Realtime Database**.

### 1. Liberando um dia para os alunos
Para desbloquear o questionário de um novo dia, o professor precisa editar a constante `LOCKS` no arquivo `index.html`:
```javascript
const LOCKS = {
  d1: true,  // Liberado
  d2: true,  // Liberado
  d3: false, // Bloqueado
  d4: false  // Bloqueado
};
```
Após alterar (mudando `false` para `true`), basta fazer um novo commit/push para o GitHub Pages ou republicar o código no Google Sites.

### 2. Acompanhamento dos Resultados
Você não precisa editar o código para contabilizar as respostas. Os votos são agregados no banco de dados automaticamente. Você pode:
- Apenas observar o termômetro na tela principal da aplicação, que já mostrará a média exata de todos os alunos que responderam.
- (Opcional) Acessar o [Console do Firebase](https://console.firebase.google.com/), abrir seu projeto e acessar o "Realtime Database" para visualizar os dados crus caso deseje exportar ou zerar testes antigos.

## 🚀 Tecnologias

- **HTML5** e **CSS3** puros (utilizando variáveis, Grid, Flexbox e animações CSS).
- **JavaScript (ES Modules)** para a lógica da aplicação.
- **Firebase Realtime Database** (BaaS) para persistência em nuvem e processamento de concorrência sem backend.
- Ícones em formato de Emojis e ilustrações em SVG.
