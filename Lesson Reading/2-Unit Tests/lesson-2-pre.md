# Readings: Unit Testing and Documentation

## 3 ways in which Unit Testing improves your codebase and productivity

### - early bug detection

By implementing unit tests, its possible to identify bugs and errors in code much earlier in the develpment cycle before the bugs effect other app segmants.

### - code quality improvement

Unit testing can ensure that every unit of code is functionoing correctly and as expected, this will prevent errors and suprise behaviours within the application

### - encouraging good programming habits

Unit tests encourage writing modular, testable and clean code, which helps the quality of the codebase.

### How would you write a unit test for a household task such as putting away laundry

- seperate laundry by color: light colored clothes go together, dark colored clothes go together, white clothes are sperated from everything else.

- seperate each color coded clothes by its material: some materials require different heats so seperate accordingly.

- set heat ranges which fit the most amount of laundry with the least delta between lowest heat recommended and highest heat recommended.

- test your groups and check if your group was entirely successful/mostly successful/barely successful/failed.

- if some clothes get corrupted check that group and identify the reason for the corruption. was it the (color/material/heat range delta) that caused the issue ?

## The art of ReadMe

### 3 reasons a quality README is just as important as quality code

1. The lack of a README file is a powerful red flag, the lack of a README means developers will need to dive into your code to understand it. Making it more likely to think less of your code/ not want to use it.
2. A README written in non predictable format or missing key elements will lead to cofusion which also lead to the same result as above (losing the want to use your code / think less of it).
3. While not always applicable, if you have a non-permissive license, stick it at the very top of your README to prevent any confusion.

### 4 crucial elements to include when writing a README for your co-developers

1. tell them what it is (with context)
2. show them what it looks like in action
3. show them how they use it
4. tell them any other relevant details
