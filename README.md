# Attendify
Attendify is a facial recognition attendance system that provides an automated and efficient way to take attendance using face recognition technology. The system captures video frames from a webcam, detects faces, matches them with known faces in the database, and updates the attendance status accordingly. The system is built using Python, OpenCV, face_recognition library, and integrated with Firebase for data storage and retrieval.

# System Overview
The Attendify system consists of the following main components:
•	main.py: This script serves as the main entry point of the application. It initializes the required libraries and frameworks, establishes connections with Firebase using service account credentials, and creates the Tkinter GUI for subject selection and date entry. It also defines the submit_attendance function, which is triggered when the user clicks the "Submit" button. This function starts the face recognition process by calling the start_face_recognition function.
•	EncodeGenerator.py: This script is responsible for generating face encodings for known student images. It reads the student images from the "Images" folder, encodes them using face_recognition library, and saves the encodings along with their corresponding student IDs to a pickle file named "EncodeFile.p". The encoded images are also uploaded to the Firebase storage bucket.
•	AddDataToDatabase.py: This script adds sample student data to the Firebase Realtime Database. It defines a dictionary with student information, such as name, major, starting year, total attendance, standing, year, and last attendance time. The script establishes a connection with Firebase and iterates over the dictionary, setting each student's data under the "Students" reference in the database.

# Facial Recognition Process
The facial recognition process in Attendify involves the following steps:
•	Face Detection: The system captures video frames from the webcam and converts them to grayscale. It uses OpenCV's face detection cascade classifier to detect faces in the grayscale frames.
•	Face Recognition: For each detected face, the system extracts the face region and encodes it using the face_recognition library. It compares the face encodings with the known encodings from the "EncodeFile.p" file. If a match is found, the system retrieves the corresponding student ID and proceeds to update the attendance.
•	Attendance Update: The system retrieves the student's information from the Firebase Realtime Database based on the student ID. It retrieves the student's image from the Firebase storage bucket. It then updates the attendance status by checking the last attendance time and increments the total attendance count if necessary. The updated attendance data is stored in the Firebase Realtime Database.

![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture1.png)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture2.png)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture3.png)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture4.png)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture5.png)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture6.png)

# Integration with Firebase
Attendify integrates with Firebase to store and retrieve student data, as well as student images. It utilizes the Firebase Admin SDK and the provided service account credentials to establish a connection with Firebase. The system accesses the Realtime Database to retrieve student information and update the attendance data. It also utilizes the Firebase storage bucket to upload and retrieve student images.

![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture7.png)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture8.png)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture9.jpg)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture10.png)

# Mobile Application Development
In addition to the Attendify project, a mobile application has been developed to provide students with easy access to their attendance information. The mobile app incorporates various features to enhance user experience and ensure the security and accuracy of attendance tracking. The following features have been implemented:
# 1. Login System
The mobile app includes a secure login system to ensure that only authorized students can access their attendance information. Users are required to provide their login credentials, such as username and password, to authenticate themselves before accessing the app's features.
# 2. Facial Recognition
Computer vision techniques have been implemented in the mobile app to perform facial recognition. When a student logs in, the app captures their face using the device's camera and matches it with the database of enrolled students. This process ensures that only registered students can access their attendance information.
# 3. Attendance Tracker
The mobile app provides students with an attendance tracking feature. After successful facial recognition, the app retrieves the student's attendance data from the database and calculates the attendance percentage based on the number of attended classes. The attendance percentage is displayed to the student, allowing them to monitor their attendance progress.
# 4. Notifications
The app includes a notification system to alert students when their attendance falls below 80%. If a student's attendance percentage reaches a critical threshold, the app sends a notification to the student, reminding them to improve their attendance to avoid any negative consequences.
# 5. Absence Tracker
Along with the attendance percentage, the mobile app also displays the number of absences for each student. This information provides students with a comprehensive overview of their attendance record and helps them keep track of their missed classes.
# 6. Debar Alert
To highlight the importance of maintaining satisfactory attendance, the mobile app includes a debar alert feature. If a student's attendance falls below the 80% threshold, the app displays a warning message indicating that the student is at risk of being debarred. This alert serves as a reminder for students to take immediate action and improve their attendance.

![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture11.jpg)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture13.jpg)
![image](https://github.com/Qalb-E-Ali/Attendify/blob/main/Picture14.jpg)

# Absent Marking Logic
The Attendify project utilizes a logic for marking the attendance status of students as "absent" by default. The status is changed to "present" only when a student is recognized by the camera during the face recognition process. Students who are not detected by the camera are automatically marked as absent.
The project incorporates the following steps to implement the absent marking logic:
1.	Default Absent Status: When the attendance process begins, the default attendance status for all students is set as "absent" in the database.
2.	Face Recognition: The project utilizes face recognition algorithms to identify and match the faces of students captured by the camera with the known faces stored in the system.
3.	Recognition and Status Update: When a student's face is successfully recognized and matched with the known faces, their attendance status is updated to "present" in real-time. This update is made in the database for the corresponding subject and date.
4.	Camera Detection: Students who are not detected by the camera or whose faces are not recognized are not updated in the attendance status. As a result, their status remains as "absent" in the database.
5.	Real-time Updates: The attendance status is continuously updated and reflected in the graphical user interface (GUI) of the application. It provides visual feedback regarding the recognition process and dynamically updates the attendance status of each student as they come in front of the camera.
By implementing this absent marking logic, the Attendify project ensures accurate attendance tracking by capturing and recording the presence or absence of students based on their face recognition during the session.
# 5. Conclusion: 
In conclusion, the Attendify system and the accompanying mobile application have been successfully developed to address the challenges of attendance management in educational institutions. The system incorporates advanced technologies such as facial recognition and database integration to streamline the attendance tracking process and provide students with real-time access to their attendance information.
By implementing facial recognition, the Attendify system ensures that only authorized students can mark their attendance, enhancing security and accuracy. The system's integration with a database allows for efficient storage and retrieval of attendance data, enabling administrators to easily manage and monitor attendance records.
The mobile application further enhances the user experience by providing students with a convenient platform to access their attendance information. The app's features, including the attendance tracker, notifications, absence tracking, and debar alerts, empower students to take ownership of their attendance and make informed decisions to improve their attendance record.
The Attendify system and mobile application offer several benefits to educational institutions. It reduces the administrative burden associated with manual attendance management, saves time and resources, and improves overall efficiency. Students benefit from real-time access to their attendance records, enabling them to track their progress and take proactive measures to meet attendance requirements.
However, it is important to note that technology is a tool, and its effectiveness ultimately depends on how it is implemented and utilized. Proper training and support for administrators, teachers, and students are crucial for the successful adoption and implementation of the Attendify system. Additionally, privacy concerns related to facial recognition and data security must be addressed through robust security measures and compliance with relevant regulations.
In conclusion, the Attendify system and mobile application represent a significant step towards modernizing attendance management in educational institutions. By leveraging technology and providing students with greater visibility and control over their attendance, the system promotes accountability, improves efficiency, and enhances the overall educational experience. With further refinement and continued support, the Attendify system has the potential to revolutionize attendance management practices and contribute to the success of students and institutions alike.
