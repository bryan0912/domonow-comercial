# 📝 Cómo agregar o editar contenido en la plataforma

> **Solo necesitas editar un archivo: `js/data.js`**
> No toques `app.html`, `index.html` ni `css/styles.css` — esos son el motor, no el contenido.

---

## 🔁 Flujo para actualizar la plataforma

```
1. Edita  js/data.js  en VSCode
2. Guarda el archivo
3. git add js/data.js
4. git commit -m "Agrego objeción X / Actualizo guion Y"
5. git push
→ Vercel redespliega automáticamente en ~30 segundos
```

---

## 🛡️ AGREGAR UNA NUEVA OBJECIÓN

Abre `js/data.js` y busca la lista que corresponda:

| Lista         | Cuándo usar                                          |
|---------------|------------------------------------------------------|
| `OBJ_FRIA`    | Objeciones en llamada en frío o prospección inicial  |
| `OBJ_CIERRE`  | Objeciones cuando el cliente ya está evaluando precio|
| `OBJ_MODULOS` | Objeciones sobre funcionalidades, capacidad, comparación |

### Plantilla para OBJ_FRIA y OBJ_MODULOS

Copia este bloque y pégalo ANTES del último `]` de la lista:

```javascript
  ,{
    icon: '❓',               // Emoji que representa la objeción
    title: 'Texto exacto de la objeción que dice el cliente',
    badge: 'Etiqueta corta',  // Ej: 'Muy común', 'Técnica', 'Precio'
    bc: 'badge-blue',         // Color: badge-blue | badge-orange | badge-green | badge-purple | badge-gold
    trasfondo: 'Qué hay detrás de esta objeción. Por qué la dice el cliente.',
    resp: '«Texto de la respuesta completa que debe dar el asesor.»',
    preguntas: [
      '«Primera pregunta de profundización»',
      '«Segunda pregunta de profundización»'   // Puedes dejar [] si no hay preguntas
    ],
    cierre: '«Frase final de cierre para este paso.»',
    estrategia: 'Consejo interno para el asesor: qué NO hacer, qué enfatizar, puntos clave.'
  }
```

### Plantilla para OBJ_CIERRE (usa enfoque doble Challenger + SPIN)

```javascript
  ,{
    icon: '❓',
    title: 'Texto exacto de la objeción',
    badge: 'Etiqueta corta',
    bc: 'badge-blue',
    challenger: '«Respuesta con enfoque Challenger: educa y reenmarcar el problema.»',
    spin: '«Respuesta con enfoque SPIN: hace preguntas que llevan al cliente a la conclusión.»',
    preguntas: [
      '«Pregunta de profundización»'
    ],
    cierre: '«Frase de cierre.»'
  }
```

---

## 💡 AGREGAR UN TIP O BUENA PRÁCTICA

Busca `const TIPS = [` en `data.js` y agrega al final de la lista:

```javascript
  ,{
    t: '🔑 Título de la tarjeta de tips',
    items: [
      'Primer consejo o punto clave',
      'Segundo consejo',
      'Tercer consejo',
      'Cuarto consejo'
    ],
    hl: false    // Cambiar a true si quieres que resalte con fondo morado
  }
```

---

## 📋 COLORES DISPONIBLES para badges (campo `bc`)

| Valor           | Color que muestra  | Cuándo usar              |
|-----------------|--------------------|--------------------------|
| `badge-blue`    | Azul               | Objeciones técnicas      |
| `badge-orange`  | Naranja            | Objeciones frecuentes    |
| `badge-green`   | Verde              | Proceso de decisión      |
| `badge-purple`  | Morado             | Resistencia al cambio    |
| `badge-gold`    | Dorado             | Etapa de cierre / precio |

---

## ✏️ EDITAR UNA OBJECIÓN EXISTENTE

1. Busca el `title` de la objeción en `data.js` con `Ctrl+F`
2. Edita solo el campo que necesitas
3. Guarda y sube

---

## ⚠️ Reglas para no romper nada

- Siempre usar **comillas simples** `'...'` para los textos, no dobles `"..."`
- Si el texto tiene un apóstrofe (`'`), reemplázalo por `` ` `` o usa `\'`
- Cada objeto `{ }` debe tener **coma antes** si viene después de otro: `, {`
- No borrar las llaves `[` y `]` que abren y cierran cada lista
- Si algo se rompe, usa `Ctrl+Z` para deshacer

---

## 🧪 Cómo probar antes de subir

1. Abre `index.html` con Live Server en VSCode
2. Haz login y ve a "Manejo de objeciones"
3. Verifica que la nueva objeción aparece correctamente
4. Si se ve bien → sube a GitHub → Vercel despliega automáticamente
