# Nut Automation Project

Automatización de configuración de NUT (Network UPS Tools) para un SAI virtual en entornos de laboratorio.

## Instalación

### 1. Clona el repositorio

```bash
git clone https://github.com/MrHummerberg/NUT-Automation-Project
cd NUT-Automation-Project
```

### 2. Instala el paquete

> **Nota sobre distribuciones Linux modernas:** En Debian 12+, Ubuntu 23.04+, Fedora 38+ y otras distros recientes, `pip install` puede mostrar el error `externally-managed-environment`. Esto se debe a PEP 668 que protege los paquetes del sistema. Usa una de las opciones siguientes:

#### Opción A: Usando pipx (Recomendado para aplicaciones CLI)

```bash
# Instalar pipx si no lo tienes
sudo apt install pipx  # Debian/Ubuntu
# o: sudo dnf install pipx  # Fedora

# Instalar el paquete
pipx install .

# Ahora puedes usar:
sudo $(which nut-setup)
```

#### Opción B: Usando un entorno virtual (venv)

```bash
# Crear y activar el entorno virtual
python3 -m venv venv
source venv/bin/activate

# Instalar el paquete
pip install .

# Usar el comando (desde el venv activado)
sudo venv/bin/nut-setup
```

#### Opción C: Sin instalación (Ejecución directa)

Si no quieres instalar nada, puedes ejecutar directamente:

```bash
sudo python3 -m nut_automation.main
```

## Notas Importantes

- El script debe ejecutarse con privilegios de **root** (sudo) ya que modifica archivos de configuración en `/etc/nut` e instala paquetes del sistema.
- El comando `nut-setup` solo está disponible después de instalar el paquete (Opción A o B). No es un comando del sistema.

## Características

- Instalación automática de `nut` y `nut-monitor`.
- Configuración de un SAI virtual (dummy-ups).
- Configuración de usuarios y permisos.
- (Opcional) Configuración de notificaciones por correo.
- Simulación de cortes de energía.
