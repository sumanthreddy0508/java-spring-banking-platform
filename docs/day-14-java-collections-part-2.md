\# Day 14 – Java Collections Part 2



\## 1. Overview



Today I continued learning Java Collections and focused on working with collection data in practical Java programs.



Day 13 covered the basic differences between:



\- List

\- Set

\- Map

\- ArrayList

\- HashSet

\- HashMap



Day 14 focused on actually working with these collections.



\### Topics covered



\- Enhanced `for` loop

\- `forEach()`

\- Lambda expressions

\- `contains()`

\- `size()`

\- `isEmpty()`

\- Adding elements

\- Removing elements

\- Updating Map values

\- `get()`

\- `containsKey()`

\- `containsValue()`

\- `keySet()`

\- `values()`

\- `entrySet()`

\- Iterating through a Map

\- `equals()`

\- `hashCode()`

\- Practical banking examples

\- Java interview questions



\---



\# 2. Enhanced `for` Loop



The enhanced `for` loop is commonly used to process every element in a collection.



Example:



```java

List<Integer> amounts = new ArrayList<>();



amounts.add(100);

amounts.add(200);

amounts.add(300);



for (Integer amount : amounts) {

&#x20;   System.out.println(amount);

}

