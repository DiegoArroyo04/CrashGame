# Giraffe Rush: Juego de Aventura

## Descripción
**Giraffe Rush** es un emocionante juego desarrollado en JavaScript que combina estrategia, suspenso y diversión. En este juego, el jugador controla a una jirafa que debe esquivar a un león mientras acumula multiplicadores de apuesta. La clave es decidir cuándo retirarse para maximizar las ganancias antes de ser atrapado.

El proyecto incorpora técnicas avanzadas como **Web Workers** para optimizar el rendimiento de carga de imágenes, asegurando una experiencia de usuario fluida y rápida.

---

## Características Principales
- **Interactividad Dinámica:** 
  - Animaciones fluidas de la jirafa y el león.
  - Botón interactivo que cambia de estado entre "Tirar" y "Parar".

- **Riesgo Progresivo:** 
  - A medida que el multiplicador crece, aumenta la probabilidad de que el león alcance a la jirafa.

- **Optimización con Web Workers:**
  - Las imágenes del juego se cargan en paralelo para minimizar el tiempo de carga inicial.

- **Traducción Multilingüe:**
  - Implementación de i18next para mostrar mensajes dinámicos en diferentes idiomas.

- **Modularidad y Escalabilidad:**
  - Código estructurado para facilitar futuras expansiones.

---

## Tecnologías Utilizadas

### Frontend
- **HTML5 y CSS3:**
  - Diseño atractivo y funcional con un enfoque en la experiencia de usuario.

- **JavaScript:**
  - Animaciones y lógica del juego.

- **jQuery:**
  - Manipulación eficiente del DOM.

### Backend y Herramientas
- **GitHub:**
  - Control de versiones y colaboración.

- **Visual Studio:**
  - Entorno de desarrollo integrado.

- **Web Workers:**
  - Manejo de procesos en paralelo para optimizar el rendimiento.

---

## Guía de Instalación

1. Clona el repositorio desde GitHub:

```bash
https://github.com/tuusuario/giraffe-rush.git
```

2. Abre el proyecto en tu editor de código preferido (por ejemplo, Visual Studio).

3. Configura un servidor local (puedes usar extensiones como Live Server).

4. Accede al juego desde tu navegador web.

---

## Cómo Jugar
1. **Inicio del Juego:** Presiona el botón "Tirar" para comenzar.
2. **Evita el León:** Observa cómo la jirafa se mueve mientras aumenta el multiplicador.
3. **Decide Cuándo Parar:** Haz clic en "Parar" antes de que el león alcance a la jirafa para obtener tus ganancias.
4. **Objetivo:** Maximiza el multiplicador sin perder tu apuesta inicial.

---

## Optimizaciones de Rendimiento
- **Carga de Imágenes con Web Workers:**
  Las imágenes del juego se cargan de manera simultánea utilizando un Web Worker, lo que reduce los tiempos de espera.

- **Probabilidad Progresiva:**
  - A medida que el multiplicador crece, la probabilidad de perder aumenta. Esto se implementó para mantener el equilibrio entre riesgo y recompensa.

---

## Código Clave: Web Worker
El siguiente código muestra cómo se utilizan los Web Workers para cargar las imágenes:

### `imageLoaderWorker.js`
```javascript
self.onmessage = async function (e) {
    const imageUrls = e.data;
    try {
        const loadedImages = await Promise.all(
            imageUrls.map(async (url) => {
                const response = await fetch(url);
                const blob = await response.blob();
                return URL.createObjectURL(blob);
            })
        );
        self.postMessage({ success: true, images: loadedImages });
    } catch (error) {
        self.postMessage({ success: false, error: error.message });
    }
};
```

---

## Ejemplo de Lógica Progresiva en el Juego
El siguiente fragmento ilustra cómo la probabilidad de perder aumenta a medida que el multiplicador crece:

```javascript
const probabilidadFin = Math.random();
const limiteMultiplicador = multiplicadorJirafa / 10; // Incremento progresivo

if (probabilidadFin < limiteMultiplicador) {
    // Fin del juego
}
```

---

## Contribuciones
Si deseas contribuir a este proyecto, por favor sigue estos pasos:
1. Haz un fork del repositorio.
2. Crea una rama para tu característica:

```bash
git checkout -b nueva-caracteristica
```

3. Realiza tus cambios y haz commit:

```bash
git commit -m "Agregué una nueva característica"
```

4. Haz un push a la rama:

```bash
git push origin nueva-caracteristica
```

5. Abre un Pull Request en GitHub.

---

## Licencia
Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para obtener más información.

---

## Contacto
- **Desarrollador:** [Tu Nombre](https://github.com/tuusuario)
- **Correo Electrónico:** tunombre@example.com
