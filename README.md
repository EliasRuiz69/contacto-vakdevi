# contacto.vakdevi-psicoterapia.com — Tarjeta digital de Mtra. Ámbar Escalante

Estructura:
- Dockerfile        → imagen nginx:alpine
- nginx.conf        → sirve el .vcf como text/vcard (necesario para iPhone)
- site/index.html   → la página
- site/ambar.vcf    → la ficha de contacto (con foto)
- site/*.png|jpg|svg → foto, logo, iconos
- qr/               → QR (PNG/SVG) y fondo de pantalla; NO se publica (el Dockerfile solo copia site/)

Despliegue en Dokploy:
1. Hostinger → DNS de vakdevi-psicoterapia.com → registro A `contacto` → IP del VPS (2.25.131.159).
2. Sube esta carpeta a un repo de GitHub (EliasRuiz69/contacto-vakdevi).
3. Dokploy → proyecto de Vak Devi → Create Service → Application → GitHub → repo + rama main.
4. Build Type: Dockerfile (ruta: Dockerfile). Deploy.
5. Domains → Add: host contacto.vakdevi-psicoterapia.com, path /, container port 80, HTTPS on, certificado Let's Encrypt.
6. Prueba: https://contacto.vakdevi-psicoterapia.com/ambar.vcf debe abrir la ficha en iPhone.

Editar datos: cambia site/ambar.vcf y/o site/index.html, haz push y redeploy.
