# Actividad 7 - Taller 1: Creación y Despliegue de un Web Service en la Nube

Este proyecto implementa un servicio web REST en Python utilizando **Flask** y la librería **yfinance** para consultar información bursátil en tiempo real. La aplicación se encuentra contenerizada mediante **Docker** y desplegada en una máquina virtual en la nube pública (**AWS EC2**).

---

## 🛠️ Tecnologías Utilizadas

* **Lenguaje:** Python 3.11
* **Framework Web:** Flask
* **Consumo de Datos:** yfinance, pandas
* **Contenerización:** Docker
* **Infraestructura Cloud:** AWS EC2 (Ubuntu 26.04 LTS)

---

## 📂 Estructura del Proyecto

```text
├── app.py              # Punto de entrada de la aplicación Flask (API REST)
├── read_value_yf.py    # Módulo de consulta de acciones bursátiles
├── requirements.txt    # Dependencias de Python
├── Dockerfile          # Especificación para la construcción del contenedor Docker
├── .gitignore          # Archivos excluidos del control de versiones
└── README.md           # Documentación del proyecto
```

---

## 🚀 Ejecución Local con Docker

1. **Construir la imagen de Docker:**
   ```bash
   docker build -t stock-market:2.0 .
   ```

2. **Ejecutar el contenedor:**
   ```bash
   docker run --rm --name stock-market -p 5000:5000 stock-market:2.0
   ```

3. **Acceder en el navegador:**
   [http://localhost:5000](http://localhost:5000)

---

## ☁️ Despliegue en AWS EC2

1. Conectarse a la instancia mediante SSH:
   ```bash
   ssh -i "demo_docker.pem" ubuntu@<IP_PUBLICA_EC2>
   ```

2. Clonar el repositorio y construir la imagen:
   ```bash
   git clone <URL_REPOSITORIO>
   cd Computacion_Distribuida
   docker build -t stock-market:2.0 .
   ```

3. Ejecutar el contenedor mapeando al puerto 80 (HTTP):
   ```bash
   docker run -d --name stock-service -p 80:5000 --restart always stock-market:2.0
   ```

4. Acceder al servicio desde el navegador web utilizando la dirección IP pública de la instancia:
   `http://<IP_PUBLICA_EC2>/`
