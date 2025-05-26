# PostgreSQL সম্পর্কিত ৫টি প্রশ্ন ও উত্তর (উদাহরণসহ)

## ১। PostgreSQL কি?

**উত্তর:**
PostgreSQL একটি শক্তিশালী ওপেন-সোর্স ডেটাবেস ম্যানেজমেন্ট সিস্টেম যা বড় এবং জটিল অ্যাপ্লিকেশনগুলোর জন্য ডেটা সংরক্ষণ ও পরিচালনা করতে ব্যবহৃত হয়।

**উদাহরণ:**
একটি ওয়াইল্ডলাইফ রিজার্ভ ডেটাবেস তৈরি করতে PostgreSQL ব্যবহার করে আমরা `rangers`, `species`, এবং `sightings` টেবিল বানাতে পারি।

---

## ২। PostgreSQL-এ ডেটাবেস স্কিমার উদ্দেশ্য কী?

**উত্তর:**
স্কিমা ডেটাবেসের কাঠামো নির্ধারণ করে। এটি অবজেক্টগুলো (যেমন টেবিল, ফাংশন) গুচ্ছাকারে সংগঠিত করে ও আলাদা রাখে।

**উদাহরণ:**
একটি স্কিমার নাম হতে পারে `wildlife_tracking`, যেখানে সব টেবিল থাকবে যেমন:
`wildlife_tracking.rangers`, `wildlife_tracking.sightings`।

---

## ৩। Primary Key এবং Foreign Key কী?

**উত্তর:**

* **Primary Key**: প্রতিটি রেকর্ডের জন্য ইউনিক আইডি।
* **Foreign Key**: অন্য টেবিলের Primary Key কে রেফার করে।

**উদাহরণ:**

```sql
-- Primary Key
CREATE TABLE rangers (
  ranger_id SERIAL PRIMARY KEY,
  name TEXT
);

-- Foreign Key
CREATE TABLE sightings (
  sighting_id SERIAL PRIMARY KEY,
  ranger_id INT REFERENCES rangers(ranger_id)
);
```

এখানে `sightings.ranger_id` হলো `rangers.ranger_id`-এর উপর নির্ভরশীল।

---

## ৪। VARCHAR এবং CHAR ডেটাটাইপের মধ্যে পার্থক্য কী?

**উত্তর:**

* **CHAR(n)**: নির্দিষ্ট দৈর্ঘ্য, অতিরিক্ত জায়গা ফাঁকা দিয়ে পূরণ করে।
* **VARCHAR(n)**: পরিবর্তনশীল দৈর্ঘ্য, যতটুকু দরকার ততটুকু জায়গা নেয়।

**উদাহরণ:**

```sql
name CHAR(10)     -- 'Tiger   '  (স্পেস সহ)
name VARCHAR(10)  -- 'Tiger'     (কেবল টেক্সট)
```

---

## ৫। SELECT স্টেটমেন্টে WHERE ক্লজের উদ্দেশ্য কী?

**উত্তর:**
WHERE ক্লজ ব্যবহার করে আপনি নির্দিষ্ট শর্ত অনুযায়ী ডেটা ফিল্টার করতে পারেন।

**উদাহরণ:**

```sql
SELECT * FROM sightings
WHERE location ILIKE '%Pass%';
```

উপরের কোয়েরিটি শুধু সেই সাইটিংগুলো দেখাবে যেখানে লোকেশন নামে "Pass" আছে, যেমন "Snowfall Pass"।
