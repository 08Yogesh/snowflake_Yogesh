CREATE OR REPLACE STAGE MANAGE_DB.external_stages.aws_stage_errorex
    url='s3://bucketsnowflakes4'

select *from MANAGE_DB.external_stages.aws_stage_errorex


 LIST @MANAGE_DB.external_stages.aws_stage_errorex;

create or replace table our_first_db.public.orders_ex(
order_id varchar(30),
amount int,
profit int,
quantity int,
category varchar(30),
subcategory varchar (30)
)

copy into our_first_db.public.orders_ex
From @MANAGE_DB.external_stages.aws_stage_errorex
file_format=(type='csv' field_delimiter=',' skip_header=1)
files=('OrderDetails_error.csv')
on_error=continue