# University-system-Documentation
create table department
(
department_id number(4) constraints depart_id_conpk primary key,
department_name varchar2(100) constraints depart_name_con unique
);


create table student 
(
student_id number(5) constraints stud_id_pk primary key ,
gender varchar2(50),
birthdate date not null,
f_name varchar2(100) not null,
l_name varchar2(100) not null,
phone_num number(20) not null,
email varchar2(100) constraints emp_email_con unique,
department_id number(4) constraints stud_depart_confk references department(department_id)
);

create table course_info 
(
course_name varchar2(100) constraints course_name_conpk primary key,
credit_hours number(4) not null
);

create table courses
(
course_id number(4) constraints course_id_conpk primary key ,
course_name varchar2(100) constraints course_name_confk references course_info(course_name),
department_id number(4) constraints department_id_confk2 references department(department_id)
);


create table student_course_grade
(
id number(4) not null ,
student_id number(5) constraints stud_id_fk references student(student_id) ,
course_id number(4) constraints course_id_confks references courses(course_id) ,
grade varchar2(100),
credit_point number(4)  ,
primary key (id ,student_id , course_id )
);

