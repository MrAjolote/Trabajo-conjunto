# Panel de enlaces

Página HTML de un solo archivo con dos columnas:

- **Enlace permanente**: un único enlace fijo y su fecha de actualización.
- **Semanas**: cada semana tiene su número, su fecha de actualización y varios enlaces. Se pueden agregar y quitar semanas y enlaces desde la propia página.

## Cómo se comparten los datos

Los datos viven en `data.json`, dentro de este mismo repositorio. La página lee ese archivo y, si tiene un token configurado, lo modifica mediante la API de GitHub (cada cambio es un commit). Así, cualquier persona desde cualquier equipo ve los mismos datos.

- **Sin token**: solo lectura.
- **Con token**: edición. Si dos personas editan a la vez y una se desactualiza, la página recarga los datos y pide repetir el cambio, para no pisar el trabajo de la otra.

## Puesta en marcha

1. Crea un repositorio **público** en GitHub (por ejemplo `panel-enlaces`) y sube `index.html`, `data.json` y `README.md` a la raíz.
2. Activa GitHub Pages: **Settings → Pages → Deploy from a branch → `main` / `(root)` → Save**.
3. La página quedará en `https://TU-USUARIO.github.io/panel-enlaces/`.

## Crear el token para editar

1. En GitHub: foto de perfil → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. **Repository access**: *Only select repositories* y elige este repositorio.
3. **Repository permissions → Contents: Read and write**.
4. Elige la caducidad más larga que permita GitHub y genera el token (empieza con `github_pat_`).
5. Abre la página, pulsa **Configurar**, pega el token y pulsa **Guardar**. El token queda solo en ese navegador.

Cada persona que deba editar necesita su propio token. Para que sea posible, agrégala en **Settings → Collaborators** del repositorio con permiso de escritura.

## Notas

- El repositorio es público, así que los enlaces y fechas también lo son. No pongas enlaces que no quieras que otros vean.
- Nunca subas un token al repositorio ni lo pegues dentro de `index.html`.
- Los cambios se ven al instante vía la API; no hay que esperar a que se actualice GitHub Pages. La página se refresca sola cada pocos minutos o con el botón **Actualizar**.
- Si ya tenías datos en la versión anterior, usa su botón **Exportar copia**, abre esta versión con tu token y usa **Importar copia**.
