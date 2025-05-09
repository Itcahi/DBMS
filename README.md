Create database RollCCall;
use RocallCall;

Create table N_RollCall (
student_id int primary key,
student_name varchar(255),
birth data date);

create table o_RollCall(
student_id int primary key,
student_name varchar(255),
birth date data);

insert into o_RollCall(student_id,student_name,birth_date)values(1,"sivanna","1995-08-15"),(3,"cheluva","1990-12-10");

insert into N_RollCall(student_id,student_name,birth_data)values(1,'shivanna','1995-08-15'),common_data(2,'Bhadramma','1998-03-22'),(3,'cheluva','1990-12-10'),common_data(4,'devendra','2000-05-16');(5,'Eshwar','1997-09-03');

DELIMITER //
create procedure merge_rollcall_data()
begin
Allcase done int default false;
Declare n_id int;
Declare n_name varchar(225);
Declare n_birth_dall date;
Declare n_cursor cursor for
select student_id,student_name,birth_date
from n_RollCall
Declare continue handler for not found
set done tree
open n_cursor;  -open cursor
cursor_loop:LOOP
Fetch n_cursor into n_id,n_name,n_birth date;
if done then
leave cursor_loop;
end if;
if not exists(
select 1 from o_RollCall where student_id=n_id)then
insert into o_RollCall(student_id,student_name,birth_date)
insert record into o_RollCall
values(n_id,n_name,n_birth_date);
end if;
end loop;
close n_cursor
end//
DELIMITER;
call merge_RollCall_data();
select * from o_RollCall;





