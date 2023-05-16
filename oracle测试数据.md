create table main_table
(
    id           nvarchar2(64),
    sex_code     varchar2(1),
    sex_name     varchar2(1),
    name         varchar2(10),
    id_card      varchar2(50),
    house_phone  varchar2(50),
    mobile       varchar2(20),
    fax          varchar2(20),
    post_code    varchar2(20),
    email        varchar2(50),
    qq           varchar2(20),
    addr         varchar2(50),
    bizdate      date,
    hospitalCode varchar2(50),
    is_delete    int
);

create sequence main_table_index
    increment by 1 --每次+1
    start with 1 --从1开始
    nomaxvalue --不限制最大值
    nominvalue --不限制最小值
    NOCYCLE --一直累加
    cache 20; --设置取值缓存数为20(默认值) 也可设置nocache - 表示不使用缓存

alter table main_table
    add constraint main_table_index primary key (id);


create or replace procedure main_table_insert as
begin
    for i in 1..50000
        loop
            --执行以下语句
            insert into main_table(ID,
                                   sex_code,
                                   sex_name,
                                   NAME,
                                   ID_CARD,
                                   HOUSE_PHONE,
                                   MOBILE,
                                   FAX,
                                   POST_CODE,
                                   EMAIL,
                                   QQ,
                                   ADDR,
                                   bizdate,
                                   hospitalCode,
                                   is_delete)
            values (main_table_index.nextval,
                    floor(dbms_random.value(0, 3)),
                    floor(dbms_random.value(0, 3)),
                    dbms_random.string('A', 6),
                    111311198305100988 + floor(dbms_random.value(0, 811311198305100988)),
                    '0' || floor(dbms_random.value(1000000001, 80000000000)),
                    10000000000 + floor(dbms_random.value(3111111111, 3999999999)),
                    '0' || floor(dbms_random.value(1000000001, 80000000000)),
                    '' || floor(dbms_random.value(100001, 999999)),
                    dbms_random.string('L', 6) || '@' || dbms_random.string('L', 4) || '.com',
                    floor(dbms_random.value(10000001, 999999999)),
                    dbms_random.string('L', 16),
                    (select to_date((select to_char(sysdate,'J') from dual) + trunc(DBMS_RANDOM.VALUE(0, 10)), 'J') from dual),
                    'HID0101',
                    0);
        end loop;
end main_table_insert;


create table detail_table
(
    id           nvarchar2(64),
    sex_code     varchar2(1),
    sex_name     varchar2(1),
    name         varchar2(10),
    id_card      varchar2(50),
    house_phone  varchar2(50),
    mobile       varchar2(20),
    fax          varchar2(20),
    post_code    varchar2(20),
    email        varchar2(50),
    qq           varchar2(20),
    addr         varchar2(50),
    bizdate      date,
    hospitalCode varchar2(50),
    is_delete    int
);

create sequence detail_table_index
    increment by 1 --每次+1
    start with 1 --从1开始
    nomaxvalue --不限制最大值
    nominvalue --不限制最小值
    NOCYCLE --一直累加
    cache 20; --设置取值缓存数为20(默认值) 也可设置nocache - 表示不使用缓存


alter table detail_table
    add constraint detail_table_index primary key (id);

create or replace procedure detail_table_insert as
begin
    for i in 1..50000
        loop
            --执行以下语句
            insert into detail_table(ID,
                                     sex_code,
                                     sex_name,
                                     NAME,
                                     ID_CARD,
                                     HOUSE_PHONE,
                                     MOBILE,
                                     FAX,
                                     POST_CODE,
                                     EMAIL,
                                     QQ,
                                     ADDR,
                                     bizdate,
                                     hospitalCode,
                                     is_delete)
            values (detail_table_index.nextval,
                    floor(dbms_random.value(0, 3)),
                    floor(dbms_random.value(0, 3)),
                    dbms_random.string('A', 6),
                    111311198305100988 + floor(dbms_random.value(0, 811311198305100988)),
                    '0' || floor(dbms_random.value(1000000001, 80000000000)),
                    10000000000 + floor(dbms_random.value(3111111111, 3999999999)),
                    '0' || floor(dbms_random.value(1000000001, 80000000000)),
                    '' || floor(dbms_random.value(100001, 999999)),
                    dbms_random.string('L', 6) || '@' || dbms_random.string('L', 4) || '.com',
                    floor(dbms_random.value(10000001, 999999999)),
                    dbms_random.string('L', 16),
                    (select to_date((select to_char(sysdate,'J') from dual) + trunc(DBMS_RANDOM.VALUE(0, 10)), 'J') from dual),
                    'HID0101',
                    0);
        end loop;
end detail_table_insert;

create table ods_detail_table
(
    id           nvarchar2(64),
    sex_code     varchar2(1),
    sex_name     varchar2(1),
    name         varchar2(10),
    id_card      varchar2(50),
    house_phone  varchar2(50),
    mobile       varchar2(20),
    fax          varchar2(20),
    post_code    varchar2(20),
    email        varchar2(50),
    qq           varchar2(20),
    addr         varchar2(50),
    bizdate      date,
    hospitalCode varchar2(50),
    is_delete    int
);

create sequence ods_detail_table_index
    increment by 1 --每次+1
    start with 1 --从1开始
    nomaxvalue --不限制最大值
    nominvalue --不限制最小值
    NOCYCLE --一直累加
    cache 20; --设置取值缓存数为20(默认值) 也可设置nocache - 表示不使用缓存


alter table ods_detail_table
    add constraint ods_detail_table_index primary key (id);

create or replace procedure ods_detail_table_insert as
begin
    for i in 1..50000
        loop
            --执行以下语句
            insert into ods_detail_table(ID,
                                     sex_code,
                                     sex_name,
                                     NAME,
                                     ID_CARD,
                                     HOUSE_PHONE,
                                     MOBILE,
                                     FAX,
                                     POST_CODE,
                                     EMAIL,
                                     QQ,
                                     ADDR,
                                     bizdate,
                                     hospitalCode,
                                     is_delete)
            values (ods_detail_table_index.nextval,
                    floor(dbms_random.value(0, 3)),
                    floor(dbms_random.value(0, 3)),
                    dbms_random.string('A', 6),
                    111311198305100988 + floor(dbms_random.value(0, 811311198305100988)),
                    '0' || floor(dbms_random.value(1000000001, 80000000000)),
                    10000000000 + floor(dbms_random.value(3111111111, 3999999999)),
                    '0' || floor(dbms_random.value(1000000001, 80000000000)),
                    '' || floor(dbms_random.value(100001, 999999)),
                    dbms_random.string('L', 6) || '@' || dbms_random.string('L', 4) || '.com',
                    floor(dbms_random.value(10000001, 999999999)),
                    dbms_random.string('L', 16),
                    (select to_date((select to_char(sysdate,'J') from dual) + trunc(DBMS_RANDOM.VALUE(0, 10)), 'J') from dual),
                    'HID0101',
                    0);
        end loop;
end ods_detail_table_insert;


begin
    TEST.MAIN_TABLE_INSERT;
    TEST.detail_table_insert;
    TEST.ods_detail_table_insert;
end;
