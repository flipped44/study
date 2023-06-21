create table user (
id int(11) not null primary key comment '用户id',
username varchar(45) not null comment '用户名',
password varchar(45) not null comment '用户密码',
name varchar(45) comment '用户姓名',
email varchar(45) not null comment '用户邮箱',
phone varchar(45) comment '用户电话',
address varchar(45) comment '用户地址',
isadmin bit(1) not null comment '是否为管理员',
isvalidate bit(1) not null comment '账户是否有效'
);
alter table user add column(
password varchar(45) not null comment '用户密码',
name varchar(45) comment '用户姓名',
email varchar(45) not null comment '用户邮箱',
phone varchar(45) comment '用户电话',
address varchar(45) comment '用户地址',
isadmin bit(1) not null comment '是否为管理员',
isvalidate bit(1) not null comment '账户是否有效'
);