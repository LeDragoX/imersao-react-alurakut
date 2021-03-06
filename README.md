# Imersão React - Alurakut

## Resume

3ª Imersão React - Projeto da Alura que volta no passado, nos ensinando a recriar o Orkut, mas com o nome de Alurakut.

- Link (Deploy na Vercel): https://alurakut-git-main-ledragox.vercel.app/login (Se o projeto continuou no ar)

## Tecnologias utilizadas

- NodeJS;
- Yarn;
- React;
- NextJS;
- Styled-Components;
- Vercel (Deploy);
- DatoCMS (Site com Gerenciador de Conteúdo);
- Ajax (Tá mais pra Ajaj);
- Nookies (NextJS Cookies);
- JWT (Json Web Token);

## Usage

Execute [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app) with [npm](https://docs.npmjs.com/cli/init) or [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/) to bootstrap the example:

```bash
# npx vs npm: Npx remove it's dependencies after creating
npx create-next-app --example with-styled-components with-styled-components-app

# Dependencies
yarn add -D babel-plugin-styled-components
yarn add datocms-client
yarn add nookies
yarn add jsonwebtoken
# Initialize project
yarn dev
```

Access [localhost:3000/](localhost:3000/) to see the result.

## Auto-generated part

Deploy it to the cloud with [Vercel](https://vercel.com/new?utm_source=github&utm_medium=readme&utm_campaign=next-example) ([Documentation](https://nextjs.org/docs/deployment)).

### Try it on CodeSandbox

[Open this example on CodeSandbox](https://codesandbox.io/s/github/vercel/next.js/tree/canary/examples/with-styled-components)

### Notes

When wrapping a [Link](https://nextjs.org/docs/api-reference/next/link) from `next/link` within a styled-component, the [as](https://styled-components.com/docs/api#as-polymorphic-prop) prop provided by `styled` will collide with the Link's `as` prop and cause styled-components to throw an `Invalid tag` error. To avoid this, you can either use the recommended [forwardedAs](https://styled-components.com/docs/api#forwardedas-prop) prop from styled-components or use a different named prop to pass to a `styled` Link.

<details>
<summary>Click to expand workaround example</summary>
<br />

**components/StyledLink.js**

```javascript
import Link from "next/link";
import styled from "styled-components";

const StyledLink = ({ as, children, className, href }) => (
  <Link href={href} as={as} passHref>
    <a className={className}>{children}</a>
  </Link>
);

export default styled(StyledLink)`
  color: #0075e0;
  text-decoration: none;
  transition: all 0.2s ease-in-out;

  &:hover {
    color: #40a9ff;
  }

  &:focus {
    color: #40a9ff;
    outline: none;
    border: 0;
  }
`;
```

**pages/index.js**

```javascript
import StyledLink from "../components/StyledLink";

export default () => (
  <StyledLink href="/post/[pid]" forwardedAs="/post/abc">
    First post
  </StyledLink>
);
```

</details>
