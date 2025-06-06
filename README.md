<div align="center"><h1>PostgreSQL</h1></div>

<div>
<h3>1. What is PostgreSQL?</h3>
উত্তরঃ PostgreSQL হলো একটি শক্তিশালী ওপেন সোর্স রিলেশনাল ডেটাবেস ম্যানেজমেন্ট সিস্টেম (RDBMS) যা SQL (Structured Query Language) এবং আরও আধুনিক ডেটা ফিচার সমর্থন করে। এটি মূলত ডেটা সংরক্ষণ, অ্যাকসেস এবং বিশ্লেষণের জন্য ব্যবহৃত হয়, বিশেষ করে এমন প্রজেক্টে যেখানে নির্ভরযোগ্যতা, পারফরম্যান্স ও ডেটার সঠিকতা অত্যন্ত গুরুত্বপূর্ণ।

<h3>কার্যক্ষমতা ও বৈশিষ্ট্য : </h3>
<li>এটি রিলেশনাল স্ট্রাকচার ফলো করে, তবে অবজেক্ট ওরিয়েন্টেড ফিচারও সাপোর্ট করে — যেমন ইনহেরিটেন্স, কাস্টম টাইপ ও ফাংশন।</li>
<li>একাধিক ইউজার একসঙ্গে কাজ করতে পারলেও এটি ডেটার সঠিকতা বজায় রাখে।</li>
<li>সিকিউরিটি ফিচারস: রোল, পারমিশন, এনক্রিপশন এবং অথেন্টিকেশন সাপোর্ট করে।</li>
<li>CHECK, UNIQUE, FOREIGN KEY, এবং NOT NULL-এর মতো constraint ব্যবহার করে ডেটার নির্ভুলতা রক্ষা করে।</li>
<li>বড় ভলিউমের ডেটা হ্যান্ডেল করতে পারে এবং নিয়মিত ব্যাকআপ/রিস্টোর অপশনও রয়েছে।</li>
<li>আধুনিক অ্যাপ্লিকেশনের জন্য JSON ডেটা টাইপ এবং Document Store অপশনও ব্যবহারযোগ্য।</li>

<h3>ব্যবহার : </h3>
<li>ওয়েব অ্যাপ্লিকেশন ডেভেলপমেন্টে (যেমন Flask, Spring Boot, Express.js)</li>
<li>ডেটা সায়েন্স ও অ্যানালিটিক্সে</li>
<li>সরকার ও বেসরকারি প্রতিষ্ঠানের ডেটা ম্যানেজমেন্টে</li>
<li>মোবাইল ও ক্লাউড ভিত্তিক অ্যাপ্লিকেশনে</li>

<h3>উদাহরণ : </h3>
</div>

```sql
CREATE TABLE wildlife (
    id SERIAL PRIMARY KEY,
    animal_name VARCHAR(100),
    location VARCHAR(150),
    seen_on DATE
);
```
<hr>
<div>
  <h3>2. What is the purpose of a database schema in PostgreSQL?</h3>
  উত্তরঃ স্কিমা (Schema) হলো PostgreSQL ডেটাবেইসের মধ্যে একটি মাল্টি-লেভেল অর্গানাইজেশনাল ইউনিট, যার মাধ্যমে ডেটাবেইসের বিভিন্ন অবজেক্ট (যেমন টেবিল, ভিউ, ফাংশন ইত্যাদি) একটি নির্দিষ্ট গোষ্ঠীতে সাজিয়ে রাখা হয়।
আমরা যেমন একটা অফিসে আলাদা আলাদা ডিপার্টমেন্ট রাখি—HR, Accounts, IT—ঠিক তেমনই স্কিমা ডেটাবেইসের "ডিপার্টমেন্ট" হিসেবে কাজ করে।

 <h3> স্কিমা ব্যবহারের কারণ:</h3>
১. পরিচ্ছন্নতা :
একটি ডেটাবেইসে শত শত টেবিল, ভিউ বা ফাংশন থাকতে পারে। স্কিমা ব্যবহার করে এগুলোকে আলাদা গ্রুপে ভাগ করে রাখা যায় এবং এতে বোঝা যায় কোন টেবিলটি কোন মডিউলের।
<br>
<br>


২. নামসংক্রান্ত দ্বন্দ্ব (Name Conflict) এড়ানো :
একই ডেটাবেইসে একাধিক টেবিলের নাম এক হতে পারে, যদি তারা ভিন্ন স্কিমায় থাকে। ফলে ডেভেলপাররা স্বাধীনভাবে মডিউল বানাতে পারেন।

উদাহরণ:

```sql
sales.customers
support.customers
```
৩. একাধিক টিমের মধ্যে কাজ ভাগ করে নেওয়া :
যদি একটি প্রজেক্টে একাধিক টিম কাজ করে, তবে প্রত্যেক টিম তাদের নিজস্ব স্কিমায় কাজ করতে পারে—একই ডেটাবেইসে থেকেও।

৪. সিকিউরিটি ও পারমিশন কন্ট্রোল :
স্কিমা ভিত্তিক পারমিশন সেট করে নির্ধারণ করতে পারা যায় কোন ইউজার বা রোল কোন স্কিমার তথ্য অ্যাক্সেস করতে পারবে।

উদাহরণ: HR টিম hr_data স্কিমা অ্যাক্সেস করতে পারবে, কিন্তু finance_data স্কিমা নয়।

৫. ডেভেলপমেন্ট, টেস্টিং ও মেইনটেন্যান্স সহজ হয় :
ইউজার চাইলে test_schema বা dev_schema তৈরি করে নতুন কোড বা ফিচার পরীক্ষা করতে পারে, মূল ডেটাবেইসের কোনো ক্ষতি ছাড়াই।
</div>

```sql

CREATE SCHEMA myapp;

CREATE TABLE myapp.users (
    id SERIAL PRIMARY KEY,
    name TEXT
);

INSERT INTO myapp.users (name)
VALUES ('Alice');

SELECT * FROM myapp.users;
```
<hr>
<div>
  <h3>3. Explain the Primary Key and Foreign Key concepts in PostgreSQL.</h3>
উত্তরঃ
<h2>Primary Key : </h2>
ডেটাবেজের প্রতিটি টেবিলে এমন একটি কলাম থাকা দরকার, যার মান (value) প্রত্যেক রেকর্ডের জন্য আলাদা হয়। এই বিশেষ কলামকেই বলা হয় Primary Key.
<br>
উদাহরণ হিসেবে , একটি ক্লাসে একই নামের অনেক শিক্ষার্থী থাকতে পারে কিন্তু একই রোল নাম্বারের ২ জন শিক্ষার্থী থাকতে পারে না. এইখানে রোল নাম্বার হচ্ছে Primary Key.
<br>
<br>

<h3>প্রাইমারি কী এর বৈশিষ্ট্য :</h3>

<li>ইউনিক (সবার জন্য ভিন্ন)</li>

<li>খালি থাকতে পারে না (NOT NULL)</li>

<li>রেকর্ড খুঁজে পেতে সহজ করে</li>
<br>
<h3>উদাহরণ :</h3>

```sql
CREATE TABLE students (
  student_roll SERIAL PRIMARY KEY,
  name VARCHAR(100)
);
```

<h2>Foreign Key : </h2>
Foreign Key হচ্ছে এমন একটি কলাম যা অন্য একটি টেবিলের Primary Key এর সাথে সম্পর্ক তৈরি করে। এটি দুটি টেবিলকে সংযুক্ত করার জন্য ব্যবহৃত হয়।
<br>
উদাহরণ হিসেবে , যেমন একজন শিক্ষার্থী তার বেতন পেমেন্ট করেছে — এখন পেমেন্টের তথ্যের সাথে আমরা সেই শিক্ষার্থীর রোল  যোগ করতে চাই। তাই payments টেবিলে student_roll  থাকবে, যা payments টেবিলের payment_id এর সাথে যুক্ত হবে। এইখানে payment_id হচ্ছে Primary Key এবং student_roll হচ্ছে Foreign Key. 
<br>
<br>

<h3>ফরেইন কী এর বৈশিষ্ট্য :</h3>

<li>অন্য টেবিলের Primary Key রেফার করে</li>

<li>দুটি টেবিলের মধ্যে সম্পর্ক তৈরি করে)</li>

<li>Null মান থাকতে পারে</li>
<br>
<h3>উদাহরণ :</h3>

```sql
CREATE TABLE payments (
  payment_id SERIAL PRIMARY KEY,
  student_roll INT REFERENCES students(student_roll),
  amount NUMERIC,
  payment_date DATE
);

```
 
</div>
<hr>
<div>
  <h2>4. What is the difference between the VARCHAR and CHAR data types?</h2>
  উত্তরঃ
  <br>
<h3>VARCHAR (Variable Length Character) :</h3>

VARCHAR হলো পরিবর্তনশীল দৈর্ঘ্যের ডেটা টাইপ। এটি এমন string রাখে যার দৈর্ঘ্য আগে থেকে নির্ধারিত সীমার মধ্যে থাকে, কিন্তু বাস্তবে যতটুকু ইনপুট হয় ততটুকুই জায়গা ব্যবহার করে।

<h3>বৈশিষ্ট্য : </h3>

<li>সর্বোচ্চ দৈর্ঘ্য নির্ধারণ করে দেওয়া যায় (যেমন VARCHAR(255)), কিন্তু ছোট ইনপুট দিলে অতিরিক্ত জায়গা নষ্ট হয় না।</li>

<li>ইনপুট ডেটা যতটুকু, ঠিক ততটুকু স্থানই নেয়।</li>

<li>স্টোরেজ efficient – ছোট ইনপুটের ক্ষেত্রে ডিস্কে কম জায়গা লাগে।</li>


<h3>উদাহরণ : </h3>

```sql
CREATE TABLE users (
  full_name VARCHAR(100),
  email VARCHAR(255)
);
```
<h3>CHAR (Fixed Length Character) :</h3>

CHAR হলো স্থির দৈর্ঘ্যের ডেটা টাইপ। যতটুকু দৈর্ঘ্য নির্ধারণ করে দেওয়া হয়, PostgreSQL সেই অনুযায়ী ঠিক সেই পরিমাণ জায়গা বরাদ্দ করে এবং প্রয়োজন হলে ইনপুটের পরে স্পেস (space) যোগ করে পূর্ণ করে।

<h3>বৈশিষ্ট্য : </h3>

<li>ইনপুট ডেটা ছোট হলেও, অতিরিক্ত জায়গা খালি স্পেস দিয়ে পূর্ণ হয়।</li>

<li>তুলনামূলকভাবে বড় স্টোরেজ নেয়, তবে পারফরম্যান্স ভালো হয় যদি সব ডেটা একই দৈর্ঘ্যের হয়।</li>

<li>সাধারণত খুব ছোট ও নির্ধারিত দৈর্ঘ্যের ডেটার জন্য উপযোগী।</li>


<h3>উদাহরণ : </h3>

```sql

CREATE TABLE country_codes (
  country CHAR(2),
  status CHAR(1)
);
```

</div>
<hr>
<div>
  <h2>5. Explain the purpose of the WHERE clause in a SELECT statement.</h2>
  উত্তরঃ
  SQL-এ WHERE ক্লজ ব্যবহার করা হয় টেবিল থেকে নির্দিষ্ট শর্ত অনুযায়ী ডেটা বের করার জন্য।  এটি  ডেটাবেজ থেকে শুধু সেই রেকর্ডগুলো বের করে এনে দেয় , যেগুলো  শর্তের সাথে  মিলে।
ডেটাবেইজে হাজার হাজার রেকর্ড থাকতে পারে। প্রতিবার যদি সব ডেটা নিয়ে আসা হয়, তাহলে প্রয়োজনীয় ডেটা খুঁজে পাওয়া কঠিন হয়ে যায়।
এই সমস্যার সমাধান দেয় WHERE ক্লজ ।
যদি WHERE ক্লজ ব্যবহার না করা হয়, তাহলে SELECT কমান্ড সব রেকর্ড (পুরো টেবিল) দেখিয়ে দেয়। কিন্তু প্রায়ই আমাদের কিছু নির্দিষ্ট তথ্যই দরকার হয়, তখন WHERE দিয়ে ফিল্টার করা হয়।

<h3>উদাহরণ : </h3>
ধরি, students নামে একটি টেবিল আছে, যেখানে ছাত্রদের নাম, বয়স, বিভাগ ইত্যাদি তথ্য আছে। কিন্তু আমাদের Rashadul Islam নামের নির্দিষ্ট শিক্ষার্থীর তথ্য প্রয়োজন। তখন স্টেটমেন্টটি শুধুমাত্র সেই রেকর্ড দেখাবে যেখানে ছাত্রের নাম Rashadul islam.

```sql
SELECT * FROM students
WHERE name = 'Rashadul Islam';
```
</div>
