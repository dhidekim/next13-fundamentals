# next15-fundamentals

Projeto de estudo com Next.js App Router focado em fundamentos de renderizacao no servidor, roteamento e boundaries entre Server e Client Components.

## Visao geral

Este repositorio demonstra:

- Nested layouts com App Router
- Route groups (ex.: `(auth)`)
- Rotas dinamicas e catch-all (ex.: `[...data]`)
- `loading.tsx` por segmento de rota
- Uso de `Suspense` para streaming parcial
- Server Components com `fetch`
- Client Components com estado local e interacao

## Tecnologias

- Next.js 15
- React 19
- TypeScript 5
- Tailwind CSS 4
- ESLint + Prettier

## Pre-requisitos

- Node.js 20+
- Yarn (ha `yarn.lock` no projeto)

## Como executar

1. Instale as dependencias:

```bash
yarn
```

2. Rode em desenvolvimento:

```bash
yarn dev
```

3. Abra no navegador:

```text
http://localhost:3000
```

## Scripts disponiveis

- `yarn dev`: inicia ambiente de desenvolvimento
- `yarn build`: gera build de producao
- `yarn start`: sobe aplicacao em modo producao
- `yarn lint`: executa lint

## Estrutura principal

```text
src/
  app/
    layout.tsx
    page.tsx
    loading.tsx
    (auth)/
      layout.tsx
      sign-in/page.tsx
      sign-up/page.tsx
    admin/
      layout.tsx
      page.tsx
      login/page.tsx
    catalog/
      loading.tsx
      page.tsx
      product/
        page.tsx
        [...data]/
          page.tsx
          add-to-cart-button.tsx
          test.tsx
  components/
    github-profile.tsx
    long-wait-component.tsx
```

## Rotas de exemplo

- `/`: home com `Suspense` e componentes assincronos
- `/sign-in` e `/sign-up`: paginas dentro do grupo `(auth)`
- `/admin` e `/admin/login`: area administrativa com layout proprio
- `/catalog`: pagina de catalogo com loading dedicado
- `/catalog/product`: pagina de produto
- `/catalog/product/123/P/M`: rota catch-all em `[...data]`

## Conceitos praticados

- **Streaming com Suspense**: a home rende partes da UI conforme dados/componentes ficam prontos
- **Segment loading**: `app/loading.tsx` e `app/catalog/loading.tsx` exibem fallback por rota
- **Server x Client Boundary**:
  - `AddToCartButton` usa `'use client'` e estado (`useState`)
  - Paginas e componentes assincronos usam renderizacao no servidor
- **Route Group**: `(auth)` organiza rotas sem afetar URL final

## Licenca

Uso educacional para estudo de Next.js.
