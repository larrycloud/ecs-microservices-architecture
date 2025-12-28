![Portada](banner-es.png)

📘 **Available languages**
- 🇪🇸 [Versión en Español](README.md)
- 🇬🇧 [English Version](README_EN.md)

---

# 🚀 Arquitectura de Microservicios en AWS con ECS y Auto Scaling

Este repositorio documenta el **diseño, despliegue y validación de una arquitectura de microservicios en AWS**, aplicando prácticas reales de **Cloud y DevOps** orientadas a entornos productivos.

El proyecto demuestra el uso de **Amazon ECS (EC2 Launch Type)**, **Application Load Balancer**, **Auto Scaling**, **Amazon ECR**, **CloudWatch** y **Route 53**, incluyendo **pruebas de carga reales** para validar el escalado automático de servicios y de infraestructura.

---

## 🎯 Concepto y Objetivo

Diseñé, implementé y documenté una **arquitectura de microservicios productiva**, compuesta por múltiples servicios (`web`, `cats`, `dogs`) desplegados en contenedores Docker sobre **ECS con instancias EC2**.

### Objetivos del proyecto

- Demostrar **dominio práctico de arquitecturas cloud escalables**
- Validar **autoescalado real** (tareas ECS + instancias EC2)
- Implementar **observabilidad y alarmas** con CloudWatch
- Documentar todo el proceso de forma **visual y profesional**

💡 *El proyecto simula un escenario real de producción, más allá de un laboratorio básico.*

---

## 🧭 Diagrama de Arquitectura

📄 **Ver imagen completa**

![Diagrama de Arquitectura ECS](architecture/Arquitectura_ECS.jpg)

### Flujo general

1️⃣ El usuario accede al dominio `ecs.devopscloud.click`  
2️⃣ **Route 53** resuelve el DNS hacia el **Application Load Balancer**  
3️⃣ El **ALB** enruta tráfico por paths hacia los microservicios (`web`, `cats`, `dogs`)  
4️⃣ **ECS** ejecuta las tareas en instancias **EC2 privadas**  
5️⃣ **Auto Scaling** ajusta tareas e instancias según la carga  
6️⃣ **CloudWatch** monitorea métricas y dispara alarmas  

---

## 🧩 Servicios AWS Utilizados

| Servicio AWS | Función |
|-------------|--------|
| **Amazon VPC** | Red aislada con subredes públicas y privadas (Multi-AZ) |
| **Amazon ECS (EC2)** | Orquestación de contenedores Docker |
| **Amazon ECR** | Almacenamiento de imágenes Docker privadas |
| **Application Load Balancer** | Balanceo de carga y routing por paths |
| **Auto Scaling Group** | Escalado automático de instancias EC2 |
| **CloudWatch** | Métricas, logs y alarmas |
| **Amazon Route 53** | DNS y dominio personalizado |

---

## 🪜 Paso a Paso (Visual y Documentado)

> 📁 Carpeta de evidencias: `docs/screenshots/`  

---

### 1️⃣ Creación de la VPC con CloudFormation

Se despliega una VPC personalizada utilizando **Infrastructure as Code**, garantizando reproducibilidad.

![Creación VPC](docs/screenshots/1_Creacion_de_VPC_con_Cloudformation.png)

---

### 2️⃣ VPC creada correctamente

![VPC creada](docs/screenshots/2_VPC_Creada.png)

---

### 3️⃣ Diagrama de la VPC

![Diagrama VPC](docs/screenshots/3_Diagrama_VPC_Creada.png)

---

### 4️⃣ Creación de repositorios en Amazon ECR

Repositorios independientes para cada microservicio.

![Repositorios ECR](docs/screenshots/4_Creacion_de_repositorios_cat_dog_web.png)

---

## 🔁 Proceso repetido para cada microservicio

⚠️ **Los pasos 5, 6 y 7 se repiten de forma idéntica para `web`, `cats` y `dogs`.**  
Solo cambia el nombre del repositorio y el contenido servido.

---

### 5️⃣ Construcción de imágenes Docker

![Build Docker](docs/screenshots/5_Creacion_de_imagen_cats.png)

---

### 6️⃣ Etiquetado de imágenes Docker

![Tag Docker](docs/screenshots/6_Etiquetado_de_imagen_cats.png)

---

### 7️⃣ Push de imágenes a Amazon ECR

![Docker Push](docs/screenshots/7_Docker_push_de_imagen_cats.png)

---

### 8️⃣ Imágenes disponibles en ECR

![Imagen en ECR](docs/screenshots/8_Imagen_cats_cargada_a_ECR.png)

---

### 9️⃣ Creación del Cluster ECS

![Cluster ECS](docs/screenshots/9_Creacion_de_cluster_ECS.png)

---

### 🔟 Definiciones de tareas ECS

![Task Definitions](docs/screenshots/10_Creacion_de_definiciones_de_tarea.png)

---

### 1️⃣1️⃣ Application Load Balancer

![ALB](docs/screenshots/11_Creacion_de_balanceador_de_carga.png)

---

### 1️⃣2️⃣ Despliegue de servicios ECS

![Servicios ECS](docs/screenshots/12_Despliegue_de_servicios.png)

---

### 1️⃣3️⃣ Acceso vía DNS del Load Balancer

![DNS ALB](docs/screenshots/13_Visualizando_desde_DNS_del_balanceador_de_carga.png)

---

### 1️⃣4️⃣ Acceso a microservicios

![Cats](docs/screenshots/14_Visualizando_desde_DNS_del_balanceador_de_carga_cats.png)  
![Dogs](docs/screenshots/15_Visualizando_desde_DNS_del_balanceador_de_carga_dogs.png)

---

### 1️⃣5️⃣ Monitoreo con CloudWatch

![CloudWatch](docs/screenshots/16_Monitorizacion_del_sistema.png)

---

### 1️⃣6️⃣ Configuración de Route 53

![Route 53](docs/screenshots/17_Creando_registro_en_route_53.png)

---

### 1️⃣7️⃣ Acceso mediante dominio personalizado

![Dominio final](docs/screenshots/18_Acceso_desde_ecs.devopscloud.click.png)

---

## 📈 Auto Scaling y Pruebas de Carga

### 1️⃣8️⃣ Autoescalado del servicio web

![Scaling ECS](docs/screenshots/19_Configuracion_escalado_de_servicio_web.png)

---

### 1️⃣9️⃣ Escalado configurado

![Scaling configurado](docs/screenshots/20_Escalado_configurado_de_servicio_web.png)

---

### 2️⃣0️⃣ Pruebas de carga con Siege

![Siege](docs/screenshots/21_Pruebas_de_carga_y_validacion_de_escalado.png)

---

### 2️⃣1️⃣ Alarma CloudWatch

![Alarma](docs/screenshots/22_Alarma_de_autoescalado_por_alta_carga_web.png)

---

### 2️⃣2️⃣ Incremento automático de tareas ECS

![ECS Scaling](docs/screenshots/23_Incremento_automatico_de_tareas_ECS_por_autoescalado.png)

---

### 2️⃣3️⃣ Ajuste del ASG

![ASG](docs/screenshots/24_Ajuste_de_capacidad_maxima_del_ASG_para_pruebas_de_escalado.png)

---

### 2️⃣4️⃣ Escalado automático de instancias EC2

![EC2 Scaling](docs/screenshots/25_Escalado_automatico_de_instancias_EC2_en_cluster_ECS.png)

---

## 🧠 Aprendizajes Clave

- Arquitecturas ECS productivas
- Autoescalado a nivel de servicio e infraestructura
- Métricas del ALB correctamente utilizadas
- Pruebas de carga reales
- Observabilidad como pilar DevOps

---

## 🧰 Habilidades Demostradas

AWS · ECS · EC2 · Docker · ECR · ALB · Auto Scaling · CloudWatch · Route 53 · Load Testing · DevOps

---

## 🙋 Autor

**Larry Andrés Rondán Manrique**  
☁️ *Cloud & DevOps Engineer*  

📬 Email: larrycloudaws@gmail.com  
🐙 GitHub: https://github.com/larrycloud  
🌍 Portafolio: https://devopscloud.click  

---

✨ *Proyecto desarrollado como práctica profesional en arquitecturas cloud escalables y automatizadas en AWS.*
