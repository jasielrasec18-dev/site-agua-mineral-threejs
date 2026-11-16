# Pale — Água de altitude 💧

Landing page conceitual de uma marca fictícia de água mineral, com uma garrafa de vidro renderizada em **3D em tempo real** com [Three.js](https://threejs.org/). A garrafa gira, se inclina e muda de lugar conforme a rolagem da página, enquanto bolhas de gás sobem simuladas quadro a quadro.

> ✨ **Feito com um único prompt.** Todo o projeto — HTML, CSS, cena 3D, shaders e simulação de bolhas — foi gerado a partir de **um só prompt** usando o **Claude Fable 5.2**, da Anthropic. Nenhuma linha foi escrita à mão depois disso: o arquivo `index.html` é exatamente o que o modelo entregou.

🔗 **Demo:** [site-agua-mineral-threejs.vercel.app](https://site-agua-mineral-threejs.vercel.app)

---

## Destaques

- **Garrafa modelada por código** — vidro, água, tampa de alumínio e menisco gerados com `LatheGeometry` a partir de um perfil matemático (base arredondada, ombro e gargalo suaves).
- **Vidro e água realistas** — a água usa `MeshPhysicalMaterial` com transmissão e índice de refração 1,333; o vidro tem opacidade guiada por Fresnel via `onBeforeCompile` (quase invisível de frente, denso nas bordas).
- **Simulação de bolhas** — 230 bolhas instanciadas (`InstancedMesh`) com ciclo de vida próprio: nascem no fundo ou na parede, crescem, sobem com velocidade proporcional ao raio, ziguezagueiam e estouram na superfície. Um shader customizado dá o brilho de borda.
- **Física reativa** — a rolagem rápida inclina a garrafa e agita as bolhas; a direção "para cima" é recalculada no espaço da garrafa, então as bolhas escorrem pela parede quando ela inclina.
- **Coreografia por rolagem** — keyframes de posição, escala, giro e cor de fundo para cada seção, com versões separadas para desktop e mobile.
- **Controle de gás interativo** — botões *Natural*, *Leve* e *Viva* alteram a quantidade de bolhas em tempo real.
- **Tipografia em 3D** — o letreiro "Pale" e o rótulo serigrafado são texturas geradas em `<canvas>` com a fonte Instrument Serif.
- **Acessível e resiliente** — respeita `prefers-reduced-motion`, usa `aria-pressed`/`aria-live` e mostra um fallback tipográfico se o WebGL não carregar.

## Tecnologias

| | |
|---|---|
| Estrutura | HTML5 semântico |
| Estilo | CSS puro (custom properties, grid, `clamp()`, `backdrop-filter`) |
| 3D | Three.js 0.160 via import map (CDN jsDelivr) |
| Shaders | GLSL (bolhas e Fresnel do vidro) |
| Fontes | Instrument Serif + Hanken Grotesk (Google Fonts) |
| Deploy | Vercel |

Sem build, sem dependências locais, sem framework: **um único arquivo `index.html`**.

## Rodando localmente

Como o projeto usa ES modules, abra-o por um servidor local (não direto pelo `file://`):

```bash
# com Node
npx serve .

# ou com Python
python -m http.server 8000
```

Depois acesse `http://localhost:3000` (serve) ou `http://localhost:8000` (Python).

## Estrutura

```
.
├── index.html   # página completa: marcação, estilos, cena 3D e simulação
└── README.md
```

## Sobre o experimento

A ideia foi testar até onde um modelo de IA chega com **um prompt só**, sem iterações: uma landing page premium, com cena 3D física e interativa, pronta para produção. O resultado está aqui, sem retoques.

## Autor

**Jasiel Rasec** — Desenvolvedor Full Stack
Petrolina, PE · [GitHub](https://github.com/jasielrasec18-dev)

---

_Pale é uma marca fictícia. Esta é uma página conceitual, sem fins comerciais._
