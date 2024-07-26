# Тема: Функции агрегирования. 

### Запросы:

1. Вывести количество преподавателей кафедры “Software Development”.

SELECT COUNT(DISTINCT Teachers.Id) FROM Teachers, Lectures, GroupsLectures, `Groups`, Departments WHERE Teachers.Id = Lectures.TeacherId AND Lectures.Id = GroupsLectures.LectureId AND GroupsLectures.GroupId = `Groups`.Id AND `Groups`.DepartmentId = Departments.Id AND Departments.Name = "Software Development";

![текст](https://sun9-64.userapi.com/impg/Z4UP42UMh4O0VYc8bcp3E1Lt2wlP0SzB2MXwvg/SaeyL6pSn4I.jpg?size=1920x1080&quality=95&sign=7ebecefc6371df22552d6b6e45eacf52&type=album)

2. Вывести количество лекций, которые читает преподаватель “Dave McQueen”.

SELECT COUNT(DISTINCT Lectures.Id) FROM Lectures, Teachers WHERE Lectures.TeacherId = Teachers.Id AND Teachers.Name = "Dave" AND Teachers.Surname = "McQueen";

![текст](https://sun9-31.userapi.com/impg/Z-U-OGieAzNeHX1Y7Au5Dg5AK70sekW2OX0Gng/nRYMZbUZxrY.jpg?size=1920x1080&quality=95&sign=ddf23dfe6a9ee5534c0108b02d2c1feb&type=album)

3. Вывести количество занятий, проводимых в аудитории “D201”.

SELECT COUNT(*) FROM Lectures WHERE LectureRoom = "D201"; 

![текст](https://sun9-16.userapi.com/impg/5xF3s_1H7uaAq8Ez5k0xy0pjBme3bhjK_cb_6g/I3ulvD0Xh1I.jpg?size=1920x1080&quality=95&sign=06a4d29c5566bda662d4ad8b1e19bb6e&type=album)

4. Вывести названия аудиторий и количество лекций, проводимых в них.

SELECT LectureRoom, COUNT(*) FROM Lectures GROUP BY LectureRoom;

![текст](https://sun9-21.userapi.com/impg/-9pTt6vS5UXqCoM_1YZxQ08Vb6CYslkGJ6IOhA/DyqufAsd-Zg.jpg?size=1920x1080&quality=95&sign=3d324ef9663bbf0f0d5bf5d677541c77&type=album)

6. Вывести среднюю ставку преподавателей факультета “Computer Science”.

SELECT AVG(DISTINCT Salary) FROM Teachers, Lectures, GroupsLectures, `Groups`, Departments, Faculties WHERE Teachers.Id = Lectures.TeacherId AND Lectures.Id = GroupsLectures.LectureId AND GroupsLectures.GroupId = `Groups`.Id AND `Groups`.DepartmentId = Departments.Id AND Departments.FacultyId = Faculties.Id AND Faculties.Name = "Computer Science";

![текст](https://sun9-75.userapi.com/impg/grIu-xgsx3HrmSxgdwtAIR51ZVkliAhGwBHQLA/5pkDCJV3AhE.jpg?size=1920x1080&quality=95&sign=be994ed60e50093c37c6fa872245391e&type=album)

8. Вывести средний фонд финансирования кафедр. 

SELECT AVG(Financing) FROM Departments;

![текст](https://sun9-59.userapi.com/impg/_fCJEoyldOnKCml0ZSaHRtNpXAw2cUS0pzBzDg/lqICZAh5Qek.jpg?size=1920x1080&quality=95&sign=a46b386b85ce9d32968a58c29e4882d9&type=album)

9. Вывести полные имена преподавателей и количество читаемых ими дисциплин.

SELECT Teachers.Name, Teachers.Surname, COUNT(DISTINCT Subjects.Id) FROM Teachers, Lectures, Subjects WHERE Teachers.Id = Lectures.TeacherId AND Lectures.SubjectId = Subjects.Id GROUP BY Teachers.Name, Teachers.Surname;

![текст](https://sun9-44.userapi.com/impg/uvwTumcUF3iZ9Oxb_oWHBj7GIxk7a3ZtXw5YqQ/Qc2LN3kaqsI.jpg?size=1920x1080&quality=95&sign=540ca3312b27add52f6e66a2dc781c7e&type=album)

10. Вывести количество лекций в каждый день недели.

SELECT DayOfWeek, COUNT(*) FROM Lectures GROUP BY DayOfWeek;

![текст](https://sun9-52.userapi.com/impg/7qnOs8YYoxOvP-D54qWHXsmkfpOAP5a7YTppbQ/mJarB5WdLmM.jpg?size=1920x1080&quality=95&sign=b86aa9e904e8e81d2b083bb93b9aabec&type=album)

11. Вывести номера аудиторий и количество кафедр, чьи лекции в них читаются.

SELECT Lectures.LectureRoom, COUNT(DISTINCT Departments.Id) FROM Lectures, GroupsLectures, `Groups`, Departments WHERE Lectures.Id = GroupsLectures.LectureId AND GroupsLectures.GroupId = `Groups`.Id AND `Groups`.DepartmentId = Departments.Id GROUP BY Lectures.LectureRoom;

![текст](https://sun9-75.userapi.com/impg/s1Fj2VNZc70y_ep--VmXsunfdjdmYbBClMZEEQ/ueDF2pYYHfw.jpg?size=1920x1080&quality=95&sign=aab5b985443c456c4410d495751c7e98&type=album)

12. Вывести названия факультетов и количество дисциплин, которые на них читаются.

SELECT Faculties.Name, COUNT(DISTINCT Subjects.Id) FROM Faculties, Departments, `Groups`, GroupsLectures, Lectures, Subjects WHERE Faculties.Id = Departments.FacultyId AND Departments.Id = `Groups`.DepartmentId AND `Groups`.Id= GroupsLectures.GroupId AND GroupsLectures.LectureId = Lectures.Id AND Lectures.SubjectId = Subjects.Id GROUP BY Faculties.Name;

![текст](https://sun9-8.userapi.com/impg/_g8PX-u46aM8W12hh8rAkC0XJXwti86xcz10Jw/Yjstlfbwo8w.jpg?size=1920x1080&quality=95&sign=ff17f44308b36e4f231d5f876387d9a1&type=album)