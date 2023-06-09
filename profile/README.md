# Parenting Together With Another Eye, A-eye

- **Member**
  - [Server](https://github.com/YONSEI-A-EYE/Server) : Yongbin Kim
  - [Mobile](https://github.com/YONSEI-A-EYE/mobile) : Kangseok Yoon
  - [ML](https://github.com/YONSEI-A-EYE/ML) : Yoojin Song
  - UI Design : Seungyeon Lim 
- **Demo Video** : [Youtube Link](https://www.youtube.com/watch?v=Ur5YIcF4LZc)
- **Landing Page** : [Link](https://yonsei-a-eye.github.io/Landing_Page/index.html)

## Service Introduction
![001](https://user-images.githubusercontent.com/76640742/228591614-4d63217a-eb06-4916-8a83-858627f1878c.png)


### Main Services
![002](https://user-images.githubusercontent.com/76640742/228591643-5e396b55-6b82-4ed6-a73f-ac34af8abbda.png)
![003](https://user-images.githubusercontent.com/76640742/228591663-5cd1d468-892c-4c6b-8edc-6b18ed8891d5.png)

- **Baby Monitor**<br>
The baby monitor is installed in the child's room or bed so caregivers can always check if their child is in dangerous. In addition, when a fall accident occurs, parents can immediately know. This will prevent infant safety accidents and reduce first aid time in case of an accident.
<br>

- **Emotion Diary**<br>
Write a dairy and we will analyze your emotion. A diary allows you to understand your emotions at a distance. It will help not to be overwhelmed by emotions. Also, the secondary caregiver can add comments to the primary caregiver's diary. The number of comments from secondary caregiver can be used as an index of interest in the primary caregiver and child care itself.
<br>

- **Parenting Advice**<br>
Did you know that each and every baby has unique temperaments? Test your child's temperament with 9 questions! According to the result, we offer personalized parenting advice. It enables parents to understand their child's temperament and take care of them. Tell A-EYE about your parenting concerns. A-EYE will provide parenting solutions based on your child's age and temperament. A-EYE can provide perfect parenting solutions for our child with generative AI.

### User Interface 
![004](https://user-images.githubusercontent.com/76640742/228591672-f44764e5-c3d9-4ad3-80e8-441fb0b186e9.png)
![제목을-입력해주세요_-005](https://user-images.githubusercontent.com/76640742/228856463-96ba7df6-3931-4fa9-87a2-0e3710c1186f.png)

![006](https://user-images.githubusercontent.com/76640742/228591716-302528d0-d61c-49d6-b7da-9cbf3db13cb0.png)
![007](https://user-images.githubusercontent.com/76640742/228591729-dafbe8ff-6f10-477e-a4f7-71912df21b90.png)

### Service Diagram
<img width="7099" alt="diagram_final" src="https://github.com/YONSEI-A-EYE/.github/assets/76640742/1bad1f23-5cbf-417d-9b8e-30e52ce47a24">


### Service Architecture
<img width="919" alt="service_architecture" src="https://github.com/YONSEI-A-EYE/.github/assets/76640742/fdad2d50-0c98-423e-b185-4120d33c9918">

- **Login** <br>
Self-login using the JWT token has been implemented, and the primary caregiver and secondary caregiver can connect account information through Verification Code.

- **Google Compute Engine - API server** <br>
It is an architecture in which A flutter receives data from a server through REST API with Spring Boot API Server.
The natural language api analyzes the received user's diary content and returns the score and magnitude values. When the score and magnitude for each sentence are returned to the spring server, it is processed as a result of the entire sentence and then the emotions are classified and handed over to the client. MySQL was used as the database. OpenAI API takes information of a child and situation as a prompt and generates advice.

- **Google Compute Engine - Detection Server** <br>
When a Raspberry Pi camera for real-time video streaming detects a fall by importing a mediapipe library, the fast api (detection server) delivers a fall detection message to the firebase cloud messaging(FCM). After receiving the message, FCM delivers a push message to the client, Flutter, and the client notifies the user.
