# Индексы
#### 1. Создать индекс к какой-либо из таблиц вашей БД
> Простой индекс по полю code_diag, для таблицы reception_doctor, чтобы группировать/отбирать данные по коду диагноза.  
<image src="https://github.com/ArinichElena/create_index/blob/main/простой.png">

#### 2. Результат команды explain, в которой используется предыдущий индекс.
<image src="https://github.com/ArinichElena/create_index/blob/main/план.png">
```xml
[
{
"Plan": {
"Node Type": "Bitmap Heap Scan",
"Parallel Aware": false,
"Async Capable": false,
"Relation Name": "reception_doctor",
"Schema": "public",
"Alias": "reception_doctor",
"Startup Cost": 5.60,
"Total Cost": 26.72,
"Plan Rows": 170,
"Plan Width": 78,
"Actual Startup Time": 0.043,
"Actual Total Time": 0.087,
"Actual Rows": 170,
"Actual Loops": 1,
"Output": ["id", "patient_id", "record_id", "doctor_id", "clinic_id", "load_date", "code_diag", "comment_doctor"],
"Recheck Cond": "((reception_doctor.code_diag)::text = 'B02.1'::text)",
"Rows Removed by Index Recheck": 0,
"Exact Heap Blocks": 19,
"Lossy Heap Blocks": 0,
"Plans": [
{
"Node Type": "Bitmap Index Scan",
"Parent Relationship": "Outer",
"Parallel Aware": false,
"Async Capable": false,
"Index Name": "idx_reception_diag",
"Startup Cost": 0.00,
"Total Cost": 5.55,
"Plan Rows": 170,
"Plan Width": 0,
"Actual Startup Time": 0.027,
"Actual Total Time": 0.027,
"Actual Rows": 170,
"Actual Loops": 1,
"Index Cond": "((reception_doctor.code_diag)::text = 'B02.1'::text)"
}
]
},
"Planning Time": 0.057,
"Triggers": [
],
"Execution Time": 0.140
}
]
```
