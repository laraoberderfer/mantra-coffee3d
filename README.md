# ☕ Mantra Coffee — Landing Page 3D

Landing page institucional e comercial da **Mantra Coffee**, marca de café especial de origem única com rastreabilidade total da cadeia produtiva.

> **100% rastreável, do produtor à sua xícara.**

---

## 📋 Visão Geral

Página única (*single page*) com cena 3D interativa em **Three.js**, construída sem frameworks de UI e sem assets externos — todos os elementos visuais são gerados proceduralmente ou via SVG inline.

| Item | Valor |
|---|---|
| Tipo | Landing page estática (HTML/CSS/JS) |
| Build | Nenhum — roda direto no navegador |
| Dependências | Three.js r160+ (CDN) |
| Assets externos | Zero |
| Deploy | GitHub Pages / Netlify / Vercel / qualquer host estático |

---

## 🎨 Identidade Visual

A paleta e o logotipo foram derivados do arquivo `image-01a1ac97-006f-71cc-858a-a316496aa902.png`.

### Paleta

| Token | Hex | Uso |
|---|---|---|
| `--bg-terra` | `#B08A7E` | Fundo principal (marrom rosado) |
| `--copper-dark` | `#8B4A2B` | Cobre escuro / títulos |
| `--copper` | `#B5651D` | Cobre metálico / acentos |
| `--copper-light` | `#C97B3F` | Gradiente foil / hover |
| `--cream` | `#F3E7DE` | Texto sobre fundo escuro |
| `--deep` | `#2A1A14` | Marrom profundo / footer |

### Logotipo

Recriado em **SVG inline** com gradiente metálico (*foil stamp*):

- Xícara estilizada com bordas superiores formando **três picos de montanha**
- **Grão de café** diagonal integrado à base
- **Alça** em linha curva fina (*line art*)
- Tipografia: `MANTRA` (caixa alta, kerning amplo, peso médio) sobre `COFFEE` (peso leve, mesma largura total)

Vantagem do SVG inline: escala sem perda, recolorível via `currentColor` e gradiente, zero requisições HTTP.

---

## 🧊 Cena 3D (Three.js)

### Geometria procedural

| Elemento | Técnica |
|---|---|
| Corpo da xícara | `LatheGeometry` (perfil por pontos) |
| Alça | `TorusGeometry` |
| Superfície do café | Cilindro com material reflexivo |
| Grãos | Esferas achatadas com sulco, em sistema de partículas |
| Vapor | `Points` com textura radial gerada em `<canvas>` |

### Iluminação

Três fontes: ambiente quente + duas pontuais (cobre e creme) + *rim light* para separar a xícara do fundo. Materiais `MeshStandardMaterial` com `metalness`/`roughness` calibrados para cerâmica e cobre.

### Interações

- **Parallax de mouse** — rotação suave da cena
- **Scroll-driven camera** — aproximação e dispersão dos grãos via interpolação de `scrollY`
- **Órbita contínua** dos grãos com `requestAnimationFrame` e delta time

### Performance

```js
renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

---

## 📋 Autoria
Professora Lara Popov Zambiasi Bazzi Oberderderfer
IFSC Câmpus Chapecó
com auxilio de AdaptaOne
