# CalTracker

Seguimiento de calorías y macros con análisis de fotos por IA (OpenAI GPT-4o-mini).

## Funcionalidades

- **Foto → Calorías**: tomás foto del plato, GPT-4o-mini estima calorías y macros
- **Ingreso manual**: para cuando no tenés foto o querés corregir
- **Peso diario**: promedio móvil 7 días, velocidad de pérdida real, sparkline
- **Ajuste adaptativo**: avisa si la pérdida es muy rápida, lenta, o estancada
- **Mifflin-St Jeor**: cálculo preciso de TDEE con factor de actividad
- **Macros configurables**: proteína sobre peso actual u objetivo, sliders para g/kg
- **Export/Import**: backup JSON de todos los datos
- **PWA offline**: funciona sin internet (excepto el análisis de fotos)

## Deploy en GitHub Pages

```bash
# Opción A: agregar a tu repo existente (ej: inst_tools)
cp -r caltracker/ tu-repo/caltracker/
cd tu-repo
git add caltracker/
git commit -m "feat: add CalTracker"
git push

# URL: https://tu-usuario.github.io/tu-repo/caltracker/

# Opción B: repo dedicado
# Crear repo "caltracker" en GitHub
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/tu-usuario/caltracker.git
git push -u origin main
# Activar GitHub Pages en Settings → Pages → main branch
```

## Instalar en iPhone

1. Abrí la URL en **Safari**
2. Tocá el ícono de **compartir** (cuadrado con flecha)
3. **Agregar a pantalla de inicio**
4. Se instala como app con ícono propio

## API Key

- La app pide tu OpenAI API key en el primer uso
- Se guarda **localmente** en localStorage de tu teléfono
- Nunca se envía a ningún servidor excepto `api.openai.com`
- Modelo: `gpt-4o-mini` → ~$0.003 por foto analizada
- Obtené tu key en [platform.openai.com/api-keys](https://platform.openai.com/api-keys)

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

Cero dependencias. Cero build. Cero backend.
