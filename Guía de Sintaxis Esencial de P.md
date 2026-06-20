# 🐍 Guía de Sintaxis Esencial de Python para Sysadmin y Redes

> Sección de consulta rápida para el desarrollo de scripts de automatización, análisis de logs, administración de sistemas y redes.

---

## 📌 Índice
1. [Fundamentos y Estructuras de Datos](#1-fundamentos-y-estructuras-de-datos)
2. [Manipulación de Archivos y Logs](#2-manipulación-de-archivos-y-logs)
3. [Interacción con el Sistema Operativo (Linux)](#3-interacción-con-el-sistema-operativo-linux)
4. [Redes y Conectividad Básica](#4-redes-y-conectividad-básica)
5. [Automatización de Equipos de Red (Netmiko)](#5-automatización-de-equipos-de-red-netmiko)

---

### 1. Fundamentos y Estructuras de Datos
```python
# Bucle FOR con rango (útil para iterar IPs o segmentos)
for i in range(1, 5):
    print(f"192.168.1.{i}")

# Condicional IF / ELSE con operadores lógicos
puerto = 443
if puerto == 80 or puerto == 443:
    print("Tráfico Web Permitido")
elif puerto == 22:
    print("Acceso SSH")
else:
    print("Puerto no identificado / Bloqueado")

# Función útil: Cálculo de Wildcard a partir de Máscara
def calcular_wildcard(mascara_red):
    octetos = mascara_red.split(".")
    wildcard = [str(255 - int(octeto)) for octeto in octetos]
    return ".".join(wildcard)

print(calcular_wildcard("255.255.255.0"))  # Resultado: 0.0.0.255

### 2. Manipulación de Archivos y Logs

import re

# Apertura segura de archivos para análisis de logs (ej. auth.log)
with open("auth.log", "r") as archivo:
    for linea in archivo:
        if "Failed password" in linea:
            # Extraer IP usando Expresiones Regulares (Regex)
            ip = re.search(r'rhost=(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})', linea)
            if ip:
                print(f"⚠️ Intento fallido desde la IP: {ip.group(1)}")

### 3. Interacción con el Sistema Operativo (Linux)

import os
import sys
import subprocess

# Verificar privilegios de Root (UID 0 en Linux)
if os.getuid() != 0:
    print("❌ Error: Este script requiere privilegios de administrador (sudo).")
    sys.exit(1)

# Ejecutar comandos de la terminal y capturar salida estándar
resultado = subprocess.run(["df", "-h", "/"], capture_output=True, text=True)
print(resultado.stdout)

### 4. Redes y Conectividad Básica

import subprocess
import requests

# Monitoreo básico de Hosts (Ping)
def verificar_host(ip):
    # -c 1 envía un solo paquete. Devuelve returncode 0 si responde.
    respuesta = subprocess.run(["ping", "-c", "1", ip], stdout=subprocess.DEVNULL)
    return f"🟢 {ip} ACTIVO" if respuesta.returncode == 0 else f"🔴 {ip} INACTIVO"

# Consulta de APIs de Red (Geolocalización de IP o datos ASN)
url = "[https://ipapi.co/8.8.8.8/json/](https://ipapi.co/8.8.8.8/json/)"
respuesta = requests.get(url)
if respuesta.status_code == 200:
    datos = respuesta.json()
    print(f"País: {datos.get('country_name')} | ISP: {datos.get('org')}")

### 5. Automatización de Equipos de Red (Netmiko)

from netmiko import ConnectHandler

# Configuración del diccionario de conexión para SSH remoto
cisco_router = {
    'device_type': 'cisco_ios',
    'host': '192.168.10.1',
    'username': 'admin',
    'password': 'TuPasswordSeguro',
    'secret': 'TuEnablePassword',  # Contraseña del modo privilegiado
}

with ConnectHandler(**cisco_router) as net_connect:
    net_connect.enable()  # Entrar a modo enable
    
    # Enviar comando de Verificación (Show)
    print(net_connect.send_command("show ip interface brief"))
    
    # Bloque de Configuración masiva (Global Config)
    comandos_config = [
        "interface GigabitEthernet0/1",
        "description Enlace Troncal hacia Switch_Core",
        "ip address 10.0.0.1 255.255.255.252"
    ]
    net_connect.send_config_set(comandos_config)


### Codigo para simular entrar en la terminal
import subprocess

# Esto equivale a escribir el comando e irónicamente presionar Enter en Ubuntu
subprocess.run(["sudo", "systemctl", "stop", "servidor_legitimo.service"])
