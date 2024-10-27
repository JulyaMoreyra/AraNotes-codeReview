# AraNotes (Clone do Notion)

![Foto AraNotes](https://cdn.discordapp.com/attachments/895030530154823720/1299852348377534504/image.png?ex=671eb555&is=671d63d5&hm=0acf6e640b0b87797f1a4abc6f8336826353df52f5231089592e511af9c3609f&)
[Acesse o site por aqui](https://aranotes.vercel.app)

## Descrição do Projeto

AraNotes é um projeto desenvolvido como parte da atividade de code review da matéria de Projeto de Software. O objetivo é criar um clone simplificado do Notion, utilizando Next.js para a interface do usuário, Convex no backend para gerenciamento de dados e Clerk para autenticação de usuários.

![Vídeo AraNotes](/assets/AraNotes%20-%20Opera%202024-10-26%2018-57-29.gif)

## Arquitetura do Projeto

- **Frontend**: O frontend é construído em Next.js, um framework React que facilita a criação de aplicações web com renderização do lado do servidor e geração de páginas estáticas. Isso garante uma melhor performance e otimização para SEO.
  
- **Backend**: O backend utiliza Convex, que oferece uma solução escalável para gerenciamento de dados em tempo real, simplificando a interação entre o frontend e o banco de dados.

- **Autenticação**: A autenticação de usuários é gerida pelo Clerk, que fornece uma interface fácil de usar para login, registro e gerenciamento de sessões, garantindo a segurança dos dados do usuário.

<br/>
<br/>
<br/>

## Clone do Repositório

### Passo 1.1 - Clonar o repositório
```
git clone https://github.com/victorreiscarlota/AraNotes.git
```

### Passo 1.2 - Instalar dependências

```
npm i -g pnpm
pnpm install
```


### Passo 1.3 - Executar o projeto

```
pnpm dev
```

- Em um novo terminal

```
pnpx convex dev
```
## Passo 2 - Configurar o .env

### 2.1 - Configuração do Convex - [Link de referência](https://docs.convex.dev/home)

### 2.2 - Configuração do Clerk - [Link de referência](https://clerk.com/docs)

### 2.3 - Configuração do Edge Store - [Link de referência](https://edgestore.dev/docs/quick-start)

# Atividade de Pull Request

### 1. **Reorganização das Pastas e Componentes por Contexto de Uso**

   - **Problema atual**: A pasta `components` contém componentes variados, como `Editor`, `Toolbar`, `icon-picker`, e outros que parecem servir a diferentes funcionalidades. Essa organização é comum, mas, em projetos maiores, uma única pasta com muitos arquivos pode dificultar a navegação e o entendimento da estrutura.
   - **Sugestão**: Organizar os componentes por domínio ou contexto de uso. Por exemplo:
     - `components/editor` para todos os componentes que fazem parte do editor de notas, como `Editor`, `Toolbar`, etc.
     - `components/marketing` para os componentes usados em páginas de marketing, como `Navbar`, `Footer`, e `Logo`.
     - `components/documents` para componentes que exibem listas de documentos ou itens específicos.
   - **Justificativa**: Essa abordagem melhora a organização, tornando o projeto mais modular e fácil de navegar. Além disso, facilita o trabalho em equipe, pois outros desenvolvedores conseguem identificar rapidamente onde estão os componentes específicos de cada funcionalidade. Também ajuda na escalabilidade, caso novos componentes sejam adicionados.

---

### 2. **Centralização de Arquivos Globais e Configurações do Next.js**

   - **Problema atual**: Arquivos como `layout.tsx`, `globals.css`, e alguns `providers` (como `theme-provider.tsx`) estão dispersos e misturados com módulos de páginas específicas.
   - **Sugestão**: Consolidar arquivos globais em uma estrutura de pasta `src`, com subpastas para organizar:
     - `src/pages`: para os arquivos de página.
     - `src/providers`: para todos os provedores de contexto.
     - `src/styles`: para arquivos de estilo globais.
     - `src/config`: para configurações de frameworks e outras dependências.
   - **Justificativa**: A estrutura centralizada facilita a navegação e torna mais evidente o que é configuração global e o que é código específico de funcionalidade. Esse modelo de estrutura melhora a clareza de onde se encontram as configurações e componentes compartilhados, o que é útil tanto para quem desenvolve quanto para novos membros que precisam entender o projeto.

---

### 3. **Modularização dos Hooks Customizados**

   - **Problema atual**: Todos os hooks estão em uma pasta única (`hooks`), o que pode ser adequado para poucos hooks, mas tende a se desorganizar conforme a aplicação cresce.
   - **Sugestão**: Agrupar hooks por categorias de uso em subpastas, como `hooks/ui`, `hooks/network`, ou `hooks/documents`. Alguns exemplos:
     - Hooks de UI ou estado visual (`use-scroll-top`, `use-cover-image`) podem ir em uma subpasta `hooks/ui`.
     - Hooks que lidam com dados de backend ou configurações (`use-settings`) poderiam estar em `hooks/network` ou `hooks/settings`.
   - **Justificativa**: Melhor organização e manutenção de código, com a possibilidade de criar hooks específicos para áreas funcionais e contextos distintos. Em uma equipe maior, isso permite que os desenvolvedores identifiquem rapidamente onde estão os hooks de um determinado tipo ou funcionalidade.

---

### 4. **Documentação Interna de Componentes e Estrutura da API**

   - **Problema atual**: Não parece haver documentação nos componentes, o que dificulta o entendimento do propósito e uso de cada módulo.
   - **Sugestão**: Adicionar breves comentários nos componentes principais ou criar um `README.md` dentro de subpastas com componentes de domínio específico. Isso pode incluir:
     - Explicações sobre a função dos componentes dentro daquela pasta.
     - Exemplos de uso, quando aplicável.
     - Notas sobre integração com outros módulos.
   - **Justificativa**: A documentação ajuda na compreensão do projeto, especialmente em áreas que envolvem lógica complexa ou em componentes reutilizáveis que outras partes do projeto dependem. Isso reduz a curva de aprendizado para novos desenvolvedores e aumenta a clareza ao revisar ou atualizar código.

---

### 5. **Consolidação de Configurações Sensíveis em uma Subpasta `config`**

   - **Problema atual**: Configurações como `next.config.js`, `tailwind.config.ts`, e `postcss.config.js` estão diretamente na raiz, o que pode misturar a estrutura de configuração com os arquivos de código.
   - **Sugestão**: Mover todas as configurações para uma pasta `config` na raiz do projeto, onde esses arquivos possam ser organizados separadamente. Esta pasta pode incluir:
     - `next.js.config` para o Next.js.
     - `tailwind.config.ts` para o Tailwind CSS.
     - Outras configurações futuras que possam surgir.
   - **Justificativa**: Organizar as configurações dessa forma ajuda a manter a raiz do projeto limpa e direcionada ao código principal, evitando misturar código de aplicação com arquivos de configuração de ambiente. Isso torna o projeto mais organizado e melhora a manutenção.

---

### 6. **Avaliação do Acoplamento com o Convex**

   - **Problema atual**: Atualmente, o código parece diretamente vinculado à API do Convex, o que significa que trocas de backend ou testes unitários podem ser mais complexos.
   - **Sugestão**: Considerar a criação de uma camada de serviço entre o frontend e o Convex para intermediar chamadas de dados. Essa camada pode ser construída com funções em arquivos dedicados a lidar com dados, usando abstrações que não dependam diretamente da implementação do Convex.
   - **Justificativa**: Desacoplar o frontend da implementação de backend melhora a flexibilidade, permitindo mudanças futuras sem grande impacto no restante do código. Além disso, essa camada de serviço facilita a criação de testes unitários mais robustos e a simulação de dados para desenvolvimento.

---

Essas mudanças propostas melhorariam a modularidade, organização e clareza do projeto, além de manter boas práticas de arquitetura que facilitam a escalabilidade e a manutenção no longo prazo.



