# 🌡️ Queridômetro – Google Classroom

**Acesse a aplicação aqui:** [https://eullerf.github.io/queridometro/](https://eullerf.github.io/queridometro/)

Uma aplicação web de avaliação de sentimentos (estilo "Termômetro") projetada para acompanhar o engajamento e as percepções dos alunos ao longo de um curso sobre o Google Classroom no SENAI.

## Objetivo

Permitir que o professor avalie diariamente o "clima" da turma de forma centralizada. A cada dia, os alunos respondem a uma pergunta rápida sobre como estão se sentindo em relação aos conteúdos apresentados. O site calcula o humor médio em **tempo real** e exibe visualmente em um termômetro animado, junto com a opção líder.

## Funcionalidades

- **Sincronização em Tempo Real (Firebase):** Quando um aluno vota, o termômetro de todos os outros alunos na sala é atualizado instantaneamente, refletindo a média real da turma sem necessidade de recarregar a página. O feedback visual da porcentagem também é otimizado localmente.
- **Múltiplos Dias (Abas):** 4 dias de avaliação pré-configurados.
- **Painel de Administração Dinâmico:** O professor controla quais dias estão visíveis/liberados para a turma diretamente na página via interface de usuário, refletindo para todos os alunos em tempo real.
- **Segurança com Firebase Auth:** O acesso ao Painel de Administração é restrito via login do Google exclusivo para o e-mail do professor autorizado (`euler.ferreira19@gmail.com`).
- **Prevenção de Votos Duplos:** Utiliza `localStorage` para impedir que o mesmo aluno vote mais de uma vez na mesma máquina no mesmo dia.
- **Termômetro Animado:** Um termômetro interativo em SVG que muda de cor (de vermelho a verde) dependendo da média dos votos (Humor Médio).

## Como Configurar e Utilizar

A aplicação roda nativamente no front-end (GitHub Pages, Google Sites), enquanto todo o armazenamento de dados, sincronismo de estado dos módulos e autenticação é gerenciado automaticamente pelo **Firebase**.

### 1. Painel de Administração (Liberando Dias)
Você não precisa mais editar o código para desbloquear os dias!
1. Acesse a aplicação e clique no botão **🛠️ Painel Admin** no canto superior direito.
2. Clique em **Login Admin** e autentique-se com sua conta Google (`euler.ferreira19@gmail.com`).
3. Uma vez logado, o painel mostrará a lista de dias. Clique no status de cada etapa (ex: "Bloqueado") para alternar instantaneamente para "Liberado". A tela dos alunos será atualizada na mesma hora!

### 2. Acompanhamento dos Resultados
Os votos são agregados no banco de dados automaticamente. Você pode:
- Apenas observar o termômetro na tela principal da aplicação, que já mostrará a média exata de todos os alunos que responderam.
- O percentual nas barras das opções é atualizado em tempo real assim que os alunos confirmam a resposta.

## Tecnologias

- **HTML5** e **CSS3** puros (utilizando variáveis, Grid, Flexbox e animações CSS).
- **JavaScript (ES Modules)** para a lógica da aplicação.
- **Firebase Realtime Database** para sincronização em tempo real dos votos e do status das etapas.
- **Firebase Authentication** para proteger o Painel Admin com conta Google.
- Ícones em formato de Emojis e ilustrações em SVG.
