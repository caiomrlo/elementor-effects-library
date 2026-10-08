# 🎨 Elementor Effects Library

Uma biblioteca open-source de efeitos visuais, interações avançadas e animações modernas para **WordPress + Elementor**.

Cada efeito inclui um **modelo JSON pronto para importação** e um **guia passo a passo com código limpo** para quem prefere montar manualmente.

---

## 📚 Efeitos Disponíveis

| Efeito | Descrição | Modelo Pronto | Código Manual | Tutorial |
| :--- | :--- | :---: | :---: | :---: |
| [**Sticky Horizontal Scroll**](./effects/StickyHorizontalScroll/README.md) | Transforma a rolagem vertical da página em rolagem horizontal suave mantendo a seção fixada na tela. | [`.json`](./effects/StickyHorizontalScroll/StickyHorizontalScroll.json) | [`code.html`](./effects/StickyHorizontalScroll/code.html) | [Guia](./effects/StickyHorizontalScroll/README.md) |

*(Novos efeitos serão adicionados continuamente!)*

---

## 📁 Estrutura do Repositório

```text
elementor-effects-library/
├── README.md                           # Índice principal e visão geral da biblioteca
└── effects/                            # Pasta contendo todos os efeitos
    └── StickyHorizontalScroll/         # Efeito de rolagem horizontal fixa
        ├── README.md                   # Documentação detalhada e link do vídeo tutorial
        ├── StickyHorizontalScroll.json # Modelo exportado pronto para o Elementor
        └── code.html                   # Código CSS e JavaScript pronto para copiar
```

---

## 🛠️ Como Utilizar os Efeitos

Você pode utilizar qualquer efeito deste repositório de duas maneiras:

### 1. Importação Direta do Modelo JSON (Mais Rápido)
1. Acesse a pasta do efeito desejado dentro de [`effects/`](./effects/).
2. Faça o download do arquivo `.json`.
3. No painel do seu WordPress, vá em **Modelos > Modelos Salvos** e clique em **Importar Modelos**.
4. Edite a página desejada com o Elementor, abra a biblioteca de modelos e insira o bloco importado.

### 2. Implementação Manual
1. Abra o arquivo `README.md` do efeito desejado ou o arquivo `code.html`.
2. Siga as instruções de hierarquia de containers e classes CSS necessárias.
3. Adicione o widget de **HTML** com o snippet de código fornecido.

---

## 🤝 Sugestões e Novos Efeitos

Quer sugerir um novo efeito ou achou algum bug?
Fique à vontade para abrir uma [Issue](../../issues) ou enviar um [Pull Request](../../pulls)!

---

## 📄 Licença

Este projeto está sob a licença [MIT](./LICENSE). Veja o arquivo [LICENSE](./LICENSE) para mais detalhes.

