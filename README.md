# SmartUrna Escolar (MVP)

Plataforma web simple (PHP + MySQL) para realizar votaciones escolares de forma segura y ágil.

## Requisitos
- XAMPP (o Apache + PHP 8 + MySQL 5.7/8)
- Navegador moderno
- Windows o Linux

## Instalación rápida (XAMPP – Windows)
1. Copia la carpeta `smarturna` dentro de `C:\xampp\htdocs\`.
2. Inicia **Apache** y **MySQL** en XAMPP Control Panel.
3. Importa `db.sql` desde **phpMyAdmin**: crea BD `smarturna` (si no se creó) y ejecuta el script.
4. Ajusta `config.php` si usas contraseña de MySQL distinta de vacío.
5. Abre en el navegador: `http://localhost/smarturna/public/`
6. Crea el **admin inicial** en `http://localhost/smarturna/public/admin/setup_admin.php`.
7. Inicia sesión en `http://localhost/smarturna/public/admin/login.php` y:
   - Crea/ajusta **Elección** y marca **activa**.
   - **Candidatos**: agrega listas y nombres.
   - **Padrón**: sube CSV con columnas `rut,nombre,curso,pin`.
8. Entrega a cada votante su **RUT** y **PIN**. Listo para votar.

## Instalación (Linux)
```bash
sudo apt install apache2 php php-mysql mariadb-server
sudo systemctl enable --now apache2 mariadb
# Copia el proyecto a /var/www/html/smarturna
# Crear BD e importar db.sql
```
Asegúrate que `config.php` apunte a tus credenciales (usuario/password de MySQL).

## Operación
- Votante ingresa con RUT + PIN → selecciona candidato → confirma voto.
- El sistema:
  - guarda voto **anónimo** (no registra id del votante en la tabla de votos),
  - marca al votante como **ha_votado=1** para bloquear doble voto.
- Resultados en **Admin → Resultados** (conteo por candidato).

## CSV de ejemplo
```
12.345.678-9,Juan Pérez,3°A,1234
11.111.111-1,Ana Ruiz,4°B,5678
```
