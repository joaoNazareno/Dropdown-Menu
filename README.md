# React + TypeScript + Vite

Este template fornece uma configuração mínima para fazer o React funcionar no Vite com HMR (Hot Module Replacement) e algumas regras do ESLint.

Atualmente, estão disponíveis dois plugins oficiais:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) usa [Babel](https://babeljs.io/) para Fast Refresh.
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) usa [SWC](https://swc.rs/) para Fast Refresh.

## Expandindo a configuração do ESLint

Se você estiver desenvolvendo uma aplicação para produção, recomendamos atualizar a configuração para habilitar regras de lint conscientes de tipos:

- Configure a propriedade `parserOptions` no nível superior desta forma:

```js
export default tseslint.config({
  languageOptions: {
    // outras opções...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

- Substitua `tseslint.configs.recommended` por `tseslint.configs.recommendedTypeChecked` ou `tseslint.configs.strictTypeChecked`.
- Opcionalmente, adicione `...tseslint.configs.stylisticTypeChecked`.
- Instale [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) e atualize a configuração:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Defina a versão do React
  settings: { react: { version: '18.3' } },
  plugins: {
    // Adicione o plugin do React
    react,
  },
  rules: {
    // outras regras...
    // Habilite as regras recomendadas
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```
