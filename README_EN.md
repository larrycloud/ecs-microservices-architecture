![Cover](banner-en.png)

📘 Available languages:
- 🇪🇸 [Spanish Version](README.md)
- 🇬🇧 [English Version](README_EN.md)

# 🚀 AWS Microservices Architecture with ECS and Auto Scaling

This repository documents the **design, deployment, and validation of a microservices architecture on AWS**, applying real-world **Cloud and DevOps best practices** oriented to production environments.

The project demonstrates the use of **Amazon ECS (EC2 Launch Type)**, **Application Load Balancer**, **Auto Scaling**, **Amazon ECR**, **CloudWatch**, and **Route 53**, including **real load testing** to validate automatic scaling of both services and infrastructure.

---

## 🎯 Concept and Objective

I designed, implemented, and documented a **production-ready microservices architecture**, composed of multiple services (`web`, `cats`, `dogs`) deployed as Docker containers on **ECS running on EC2 instances**.

Project goals:

- Demonstrate **hands-on expertise in scalable cloud architectures**
- Validate **real auto scaling** (ECS tasks + EC2 instances)
- Implement **monitoring and alerting** with CloudWatch
- Provide **clear, visual, and professional documentation**

💡 *This project simulates a real production scenario beyond a basic lab setup.*

---

## 🧭 Architecture Diagram

📄 **View full image:**

![ECS Architecture Diagram](architecture/Arquitectura_ECS.jpg)

Architecture flow:

1️⃣ Users access the domain `ecs.devopscloud.click`  
2️⃣ **Route 53** resolves DNS to the **Application Load Balancer**  
3️⃣ The **ALB** routes traffic by path to microservices (`web`, `cats`, `dogs`)  
4️⃣ **ECS** runs tasks on private **EC2 instances**  
5️⃣ **Auto Scaling** adjusts tasks and instances based on load  
6️⃣ **CloudWatch** monitors metrics and triggers alarms  

---

## 🧩 AWS Services Used

| AWS Service | Main Function |
|------------|---------------|
| **Amazon VPC** | Isolated network with public and private subnets (Multi-AZ). |
| **Amazon ECS (EC2)** | Docker container orchestration. |
| **Amazon ECR** | Private Docker image registry. |
| **Application Load Balancer** | Load balancing and path-based routing. |
| **Auto Scaling Group** | Automatic EC2 instance scaling. |
| **CloudWatch** | Metrics, logs, and scaling alarms. |
| **Amazon Route 53** | DNS and custom domain management. |

---

## 🪜 Step-by-Step (Visual and Documented)

> 📁 Evidence folder: `docs/screenshots/`  

---

### **1️⃣ VPC Creation using CloudFormation**
A custom VPC is deployed using **Infrastructure as Code**, ensuring reproducibility.

📸 **Evidence:**  
![VPC Creation](docs/screenshots/1_Creacion_de_VPC_con_Cloudformation.png)

---

### **2️⃣ VPC Successfully Created**
📸 **Evidence:**  
![VPC Created](docs/screenshots/2_VPC_Creada.png)

---

### **3️⃣ VPC Architecture Diagram**
📸 **Evidence:**  
![VPC Diagram](docs/screenshots/3_Diagrama_VPC_Creada.png)

---

### **4️⃣ Amazon ECR Repository Creation**
Independent repositories are created for each microservice.

📸 **Evidence:**  
![ECR Repositories](docs/screenshots/4_Creacion_de_repositorios_cat_dog_web.png)

---

## 🔁 Repeated Process per Microservice

⚠️ **Steps 5, 6, and 7 are repeated identically for `web`, `cats`, and `dogs`.**  
Only the repository name and application content change.

---

### **5️⃣ Docker Image Build**
📸 **Example (cats):**  
![Docker Build](docs/screenshots/5_Creacion_de_imagen_cats.png)

---

### **6️⃣ Docker Image Tagging**
📸 **Example (cats):**  
![Docker Tag](docs/screenshots/6_Etiquetado_de_imagen_cats.png)

---

### **7️⃣ Push Docker Image to Amazon ECR**
📸 **Example (cats):**  
![Docker Push](docs/screenshots/7_Docker_push_de_imagen_cats.png)

---

### **8️⃣ Images Available in ECR**
📸 **Evidence:**  
![Image in ECR](docs/screenshots/8_Imagen_cats_cargada_a_ECR.png)

---

### **9️⃣ ECS Cluster Creation**
📸 **Evidence:**  
![ECS Cluster](docs/screenshots/9_Creacion_de_cluster_ECS.png)

---

### **🔟 ECS Task Definitions**
📸 **Evidence:**  
![Task Definitions](docs/screenshots/10_Creacion_de_definiciones_de_tarea.png)

---

### **1️⃣1️⃣ Application Load Balancer Creation**
📸 **Evidence:**  
![ALB](docs/screenshots/11_Creacion_de_balanceador_de_carga.png)

---

### **1️⃣2️⃣ ECS Services Deployment**
📸 **Evidence:**  
![ECS Services](docs/screenshots/12_Despliegue_de_servicios.png)

---

### **1️⃣3️⃣ Access via Load Balancer DNS**
📸 **Evidence:**  
![ALB DNS](docs/screenshots/13_Visualizando_desde_DNS_del_balanceador_de_carga.png)

---

### **1️⃣4️⃣ Microservices Access**
📸 **Evidence:**  
![Cats](docs/screenshots/14_Visualizando_desde_DNS_del_balanceador_de_carga_cats.png)  
![Dogs](docs/screenshots/15_Visualizando_desde_DNS_del_balanceador_de_carga_dogs.png)

---

### **1️⃣5️⃣ Monitoring with CloudWatch**
📸 **Evidence:**  
![CloudWatch](docs/screenshots/16_Monitorizacion_del_sistema.png)

---

### **1️⃣6️⃣ Route 53 Configuration**
📸 **Evidence:**  
![Route 53](docs/screenshots/17_Creando_registro_en_route_53.png)

---

### **1️⃣7️⃣ Access via Custom Domain**
📸 **Evidence:**  
![Final Domain](docs/screenshots/18_Acceso_desde_ecs.devopscloud.click.png)

---

## 📈 Auto Scaling and Load Testing

### **1️⃣8️⃣ Web Service Auto Scaling Configuration**
📸 **Evidence:**  
![ECS Scaling](docs/screenshots/19_Configuracion_escalado_de_servicio_web.png)

---

### **1️⃣9️⃣ Scaling Configuration Applied**
📸 **Evidence:**  
![Scaling Configured](docs/screenshots/20_Escalado_configurado_de_servicio_web.png)

---

### **2️⃣0️⃣ Load Testing with Siege**
📸 **Evidence:**  
![Siege Test](docs/screenshots/21_Pruebas_de_carga_y_validacion_de_escalado.png)

---

### **2️⃣1️⃣ CloudWatch Alarm Triggered**
📸 **Evidence:**  
![Alarm Triggered](docs/screenshots/22_Alarma_de_autoescalado_por_alta_carga_web.png)

---

### **2️⃣2️⃣ Automatic ECS Task Scaling**
📸 **Evidence:**  
![ECS Task Scaling](docs/screenshots/23_Incremento_automatico_de_tareas_ECS_por_autoescalado.png)

---

### **2️⃣3️⃣ Auto Scaling Group Capacity Adjustment**
📸 **Evidence:**  
![ASG Adjustment](docs/screenshots/24_Ajuste_de_capacidad_maxima_del_ASG_para_pruebas_de_escalado.png)

---

### **2️⃣4️⃣ EC2 Instance Auto Scaling**
📸 **Evidence:**  
![EC2 Scaling](docs/screenshots/25_Escalado_automatico_de_instancias_EC2_en_cluster_ECS.png)

---

## 🧠 Key Learnings

- Production-grade ECS architecture design
- Dual-level auto scaling (services + infrastructure)
- Correct use of ALB metrics for scaling
- Real load testing validation
- Observability as a DevOps pillar ✨

---

## 🧰 Skills Demonstrated

AWS · ECS · EC2 · Docker · ECR · ALB · Auto Scaling · CloudWatch · Route 53 · Load Testing · DevOps

---

## 🙋 Author

**Larry Andrés Rondán Manrique**  
☁️ *Cloud & DevOps Engineer*  

📬 Email: larrycloudaws@gmail.com  
🐙 GitHub: https://github.com/larrycloud  
🌍 Portfolio: https://devopscloud.click  

---

✨ *Project developed as a professional practice in scalable and automated cloud architectures on AWS.*
