# CalTracker

Seguimiento de calorías y macros con análisis de fotos por IA.

**100% gratis.** Usa Google Gemini Flash (free tier, sin tarjeta de crédito).

## Funcionalidades

- **Foto → Calorías**: tomás foto del plato, Gemini Flash estima calorías y macros
- **Ingreso manual**: para cuando no tenés foto o querés corregir
- **Peso diario**: promedio móvil 7 días, velocidad de pérdida real, sparkline
- **Ajuste adaptativo**: avisa si la pérdida es muy rápida, lenta, o estancada
- **Mifflin-St Jeor**: cálculo preciso de TDEE con factor de actividad
- **Macros configurables**: proteína sobre peso actual u objetivo, sliders para g/kg
- **Export/Import**: backup JSON de todos los datos
- **PWA offline**: funciona sin internet (excepto el análisis de fotos)

## Deploy en GitHub Pages

```bash
# Crear repo "caltracker" en GitHub, subir los 4 archivos, activar Pages
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/TU-USUARIO/caltracker.git
git push -u origin main
# Settings → Pages → main branch → Save
```

## Instalar en iPhone

1. Abrí la URL en **Safari**
2. Tocá el ícono de **compartir** (cuadrado con flecha ↑)
3. **Agregar a pantalla de inicio**
4. Se instala como app con ícono propio

## API Key (gratis)

1. Andá a [aistudio.google.com](https://aistudio.google.com)
2. Iniciá sesión con tu cuenta Google
3. Hacé clic en **"Get API key"** → **"Create API key"**
4. Copiá la key (empieza con `AIza...`)
5. Pegala en la app (Config → API)

**No requiere tarjeta de crédito.** El free tier de Gemini Flash permite ~1,000 requests/día.
Para 3-5 fotos de comida diarias, es prácticamente ilimitado.

## Fórmulas

```
BMR (Mifflin-St Jeor):
  Hombre: 10 × peso(kg) + 6.25 × altura(cm) − 5 × edad + 5
  Mujer:  10 × peso(kg) + 6.25 × altura(cm) − 5 × edad − 161

TDEE = BMR × factor de actividad
Objetivo = TDEE × (1 − déficit%)
Proteína(g) = peso_ref × g/kg
Grasa(g) = peso × g/kg
Carbos(g) = (Objetivo − Proteína×4 − Grasa×9) ÷ 4
```

## Estructura

```
caltracker/
├── index.html      ← App completa (HTML + CSS + JS, sin build)
├── manifest.json   ← PWA manifest
├── sw.js           ← Service worker (cache offline)
└── README.md
```

Cero dependencias. Cero build. Cero backend. Cero costo.
