# Sticky Horizontal Scroll (Rolagem Horizontal Fixa)

Efeito moderno onde a rolagem vertical tradicional da página é convertida suavemente em rolagem horizontal de cards/elementos, mantendo a seção fixada na tela até que todos os itens tenham sido exibidos.

---

## 📺 Vídeo Tutorial

Assista ao passo a passo completo no YouTube:

[![Assistir no YouTube](https://img.shields.io/badge/YouTube-Assistir_Tutorial-red?style=for-the-badge&logo=youtube)](https://www.youtube.com/watch?v=yKLYOYL0pKA)

---

## 📦 Arquivos deste Efeito

- [`StickyHorizontalScroll.json`](./StickyHorizontalScroll.json): Modelo pronto para importar diretamente no Elementor.
- [`code.html`](./code.html): Arquivo limpo com o CSS e JavaScript para quem for montar manualmente.

---

## 🚀 Como Usar

Você pode implementar este efeito de duas formas: **Importando o Modelo Pronto** ou **Criando Manualmente**.

### Método 1: Importar o Modelo Pronto (Recomendado)

1. Baixe o arquivo [`StickyHorizontalScroll.json`](./StickyHorizontalScroll.json).
2. No painel do WordPress, vá em **Modelos > Modelos Salvos** (ou direto pelo editor do Elementor).
3. Clique em **Importar Modelos** e selecione o arquivo baixado.
4. Abra a página onde deseja usar o efeito no Elementor e insira o modelo importado via biblioteca de modelos da página.
5. Personalize os textos, imagens e cores dos cards como desejar!

---

### Método 2: Criar Manualmente Passo a Passo

Caso queira montar a estrutura do zero com seus próprios containers:

#### 1. Estrutura de Containers (Flexbox)

Monte a seguinte hierarquia no Elementor:

```text
[Container] Wrapper (Classe: horizontalScroll_wrapper)
 └── [Container] Sticky (Classe: horizontalScroll_sticky)
      ├── [Container] Cabeçalho / Título (Opcional)
      ├── [Container] Scroll Element (Classe: horizontalScroll_scrollElement)
      │    ├── [Container] Card 1
      │    ├── [Container] Card 2
      │    ├── [Container] Card 3
      │    └── ...
      └── [Widget] HTML (Código CSS + JS)
```

#### 2. Configurações de Cada Container

| Container | Configurações Principais | Classe CSS |
| :--- | :--- | :--- |
| **Wrapper** | - Largura total<br>- Altura mínima: `500vh` (quanto maior, mais lenta a rolagem vertical necessária para percorrer os cards) | `horizontalScroll_wrapper` |
| **Sticky** | - Largura total<br>- Altura mínima: `100vh`<br>- Aba **Avançado > Efeitos de Movimento**: Definir **Fixo (Sticky)** como **Superior (Top)** e manter marcado *Manter fixo até o fim do container pai* | `horizontalScroll_sticky` |
| **Scroll Element** | - Direção: **Linha (Row)**<br>- Quebra de linha (Wrap): **Sem quebra (No Wrap)**<br>- Overflow: **Oculto (Hidden)** | `horizontalScroll_scrollElement` |
| **Cards Internos** | - Definir largura fixa (ex: `30%` ou `400px` no Desktop) | — |

---

#### 3. Código (Copia e Cola)

Adicione um widget **HTML** dentro do container e cole o seguinte código:

```html
<style>
.horizontalScroll_scrollElement > * {
  flex-shrink: 0 !important;
}
</style>

<script>
document.addEventListener('DOMContentLoaded', () => {
  const containers = document.querySelectorAll('.horizontalScroll_wrapper');

  containers.forEach((container) => {
    const sticky = container.querySelector('.horizontalScroll_sticky');
    const scrollElement = container.querySelector('.horizontalScroll_scrollElement');

    if (!sticky || !scrollElement) return;

    let currentScroll = 0;
    let targetScroll = 0;
    const ease = 0.08; // Ajuste a suavidade (valores menores = mais suave/lento)

    function updateScroll() {
      const containerRect = container.getBoundingClientRect();
      const containerHeight = container.offsetHeight;
      const stickyHeight = sticky.offsetHeight;

      const totalVerticalDistance = containerHeight - stickyHeight;

      if (totalVerticalDistance <= 0) return;

      const scrollProgress = -containerRect.top / totalVerticalDistance;
      const clampedProgress = Math.min(Math.max(scrollProgress, 0), 1);

      const maxHorizontalScroll = scrollElement.scrollWidth - scrollElement.clientWidth;

      targetScroll = clampedProgress * maxHorizontalScroll;

      currentScroll += (targetScroll - currentScroll) * ease;

      scrollElement.scrollLeft = currentScroll;

      requestAnimationFrame(updateScroll);
    }

    requestAnimationFrame(updateScroll);
  });
});
</script>
```

---

## ⚙️ Customização e Ajustes

- **Suavidade da rolagem (`ease`)**:
  No script, altere a constante `const ease = 0.08;`.
  - Valores menores (ex: `0.04`): movimento mais suave e deslizante (inércia maior).
  - Valores maiores (ex: `0.15` ou `1.0`): resposta mais imediata e menos amortecida.
- **Duração do percurso**:
  Ajuste a altura mínima (`min-height`) do container `horizontalScroll_wrapper`. Se tiver muitos cards, aumente para `600vh` ou `700vh`.
- **Responsividade (Mobile)**:
  Nos dispositivos móveis, você pode ajustar a largura dos cards para `80%` ou `85%` para que o usuário veja parte do próximo card indicando a continuidade horizontal.

---

[← Voltar para a Biblioteca de Efeitos](../../README.md)
