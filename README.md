# 🛒 Retail CAD Pro 4.0

Suite profesional de diseño arquitectonico 2D y 3D en tiempo real para layout de supermercados, auditoria de pasillos, simulacion de flujos de clientes y exportacion a AutoCAD DXF.

## 🚀 Requisitos para Despliegue en Render

### Opcion 1: Static Site (Sitio Estatico - Recomendado y Gratis)
- **Build Command:** (dejar vacio o echo Build OK)
- **Publish Directory:** .
- **Auto-Deploy:** Yes

### Opcion 2: Web Service (Node.js)
- **Runtime:** Node
- **Build Command:** npm install
- **Start Command:** npm start
- **Variables de Entorno (Environment Variables):**
  - PORT: 10000
  - SUPABASE_URL: https://gxnwyeczuwiopjbwzxjw.supabase.co
  - SUPABASE_ANON_KEY: (Tu clave anon/public de Supabase)

## ☁️ Integracion con Supabase
- **Project ID:** gxnwyeczuwiopjbwzxjw
- **API URL:** https://gxnwyeczuwiopjbwzxjw.supabase.co

## 🛠️ Ejecucion Local
`ash
git clone https://github.com/sanguti95-blip/Retail-cad-pro.git
cd Retail-cad-pro
npm start
`
Abrir en el navegador: http://localhost:3000
