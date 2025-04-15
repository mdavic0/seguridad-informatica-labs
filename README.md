# Lab 0 - Introducción práctica al ambiente de laboratorio
El objetivo del lab 0 es comenzar a familiarizarse con el entorno de pruebas (Kali Linux + Metasploitable), e iniciar prácticas reales de reconocimiento de vulnerabilidades.

# Instalación de Kali Linux en Máquina Virtual (Ubuntu)

Este instructivo te guía paso a paso para instalar Kali Linux en una máquina virtual usando VirtualBox sobre Ubuntu.

---

## Ventajas de usar una VM

- No modifica tu sistema principal.
- Entorno completo y aislado para prácticas de hacking ético.
- Fácil de eliminar o reinstalar si algo sale mal.
- Permite crear snapshots y volver atrás ante errores.

---

## Pasos para la instalación

### 1. Instalá VirtualBox

Abrí una terminal y ejecutá:

```bash
sudo apt update
sudo apt install virtualbox
```

---

### 2. Descargá la imagen de Kali para VirtualBox

Desde el sitio oficial:

[https://www.kali.org/get-kali/#kali-virtual-machines](https://www.kali.org/get-kali/#kali-virtual-machines)

- Seleccioná la opción "Kali Linux VirtualBox 64-bit".
- Descargarás un archivo `.7z` que contiene la imagen `.ova`.

Descomprimilo con:

```bash
sudo apt install p7zip-full
7z x kali-linux-*.7z
```

---

### 3. Importá la imagen en VirtualBox
1. Al descomprimir vas a ver dos archivos con extensión .vbox y .vdi.
2. Hacé doble click en el archivo con extensión .vbox y esto automáticamente te carga la imagen de Kali linux en VirtualBox. 

OBS: Si al descomprimir obtenés un archivo .ova entonces seguí los siguentes pasos:
1. Abrí VirtualBox.
2. Menú `Archivo` → `Importar servicio virtualizado`.
3. Seleccioná el archivo `.ova` que descomprimiste.
4. En la pantalla de configuración, podés ajustar:
   - **Nombre de la máquina**.
   - **Cantidad de memoria RAM**: se recomienda al menos **2 GB** (2048 MB).
   - **Cantidad de CPU**: mínimo 2 núcleos si tu equipo lo permite.
   - **Red**: Modo NAT por defecto es suficiente.

Hacé clic en `Importar` y esperá a que termine el proceso.

---

### 4. Iniciá la máquina virtual

Una vez importada:

- Seleccioná la VM y hacé clic en **Iniciar**.
- Usuario por defecto: `kali`
- Contraseña: `kali`

---


# Instalación de Metasploitable en VirtualBox

## 📥 Paso 1: Descargar Metasploitable

1. Ir al sitio oficial del proyecto:  
   [https://sourceforge.net/projects/metasploitable/](https://sourceforge.net/projects/metasploitable/)

2. Descargar el archivo `.zip` de **Metasploitable 2**.

3. Extraer el `.zip`. Deberías obtener un archivo `.vmdk` (imagen de disco virtual).

---

## 💻 Paso 2: Crear una nueva máquina virtual en VirtualBox

1. Abrir **VirtualBox** y hacer clic en **"Nueva"**.

2. Configurar los siguientes parámetros:

   - **Nombre**: `Metasploitable`
   - **Tipo**: `Linux`
   - **Versión**: `Ubuntu (32-bit)`
   - **Memoria RAM**: `512 MB` o más (según disponibilidad)

3. En la sección **Disco duro**:
   - Elegir: **"Usar un archivo de disco duro virtual existente"**
   - Seleccionar el archivo `.vmdk` que descargaste.

---

# 🌐 Configurar red interna (para comunicarse con Kali)

1. Con la VM apagada, ir a **Configuración > Red**.

2. En **Adaptador 1**:
   - Activar: ✔️ "Habilitar adaptador de red"
   - Modo: `Red interna`
   - Nombre de red: `lab-hacking` (o el nombre que uses también en Kali)

3. Repetir lo mismo en la VM de **Kali Linux** para que se comuniquen entre sí.

---

# ▶️Iniciar la VM

1. Iniciar la VM de **Metasploitable** desde VirtualBox.

2. Cuando aparezca el login, usar las siguientes credenciales por defecto:

   - **Usuario**: `msfadmin`
   - **Contraseña**: `msfadmin`

3. ¡Listo! Ya tenés una máquina vulnerable lista para practicar.

---

# 🧪 Verificar conectividad desde Kali (opcional)

Desde la VM de **Kali Linux**, ejecutar:

```bash
ping <IP_de_Metasploitable>
