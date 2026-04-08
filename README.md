![Estado](https://img.shields.io/badge/Estado-En%20proceso-yellow)
# GNS3 + Hipervisores

## Objetivo
Implementar y analizar laboratorios de red avanzados usando GNS3 en Windows 11, integrando VirtualBox (Tipo 2) y VMware ESXi (Tipo 1).

---

## 1. Arquitectura de Virtualización en Windows 11

### Aislamiento de Núcleo y VBS
El aislamiento de núcleo y la seguridad basada en virtualización (VBS) protegen el sistema, pero pueden afectar el rendimiento de herramientas como GNS3.

### Activación de VT-x / AMD-V
Se debe activar desde la BIOS.
Para verificar en Windows:
- Administrador de tareas → Rendimiento → CPU → Virtualización: Habilitado

---

## 2. GNS3 VM: El Motor de Simulación

### KVM
KVM permite acelerar la virtualización.
Debe aparecer como:
**KVM support: True**

### Recursos
- CPU: 2 o más núcleos
- RAM: 4GB mínimo

---

## 3. Integración con VirtualBox

### Red Host-Only
Permite comunicación entre GNS3 y la VM.

### Modo Promiscuo
Permite capturar todo el tráfico de red (importante para capa 2).

---

## 4. Integración con VMware ESXi

### Cliente-Servidor
GNS3 se conecta desde la PC a un servidor ESXi remoto.

### Seguridad
Configurar:
- Promiscuous mode: Accept
- MAC address changes: Accept

---

## 5. Troubleshooting

| Error | Causa | Solución |
|------|------|--------|
| KVM False | Virtualización no activa | Activar VT-x en BIOS |
| No conexión | Red mal configurada | Revisar Host-Only |
| Error puerto 3080 | Firewall bloquea | Abrir puertos |
