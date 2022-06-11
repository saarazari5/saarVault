---
dateCreated: "2022-06-11 15:48"
tags: [data structures, java]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Tree map]]
The TreeMap in Java is used to implement [Map interface](https://www.geeksforgeeks.org/map-interface-java-examples/) and [NavigableMap](https://www.geeksforgeeks.org/navigablemap-interface-in-java-with-example/) along with the AbstractMap Class. The map is sorted according to the natural ordering of its keys, or by a [Comparator](https://www.geeksforgeeks.org/comparator-interface-java/) provided at map creation time, depending on which constructor is used. This proves to be an efficient way of sorting and storing the key-value pairs. The storing order maintained by the treemap must be consistent with equals just like any other sorted map, irrespective of the explicit comparators. The treemap implementation is not synchronized in the sense that if a map is accessed by multiple threads, concurrently and at least one of the threads modifies the map structurally, it must be synchronized externally. 

![](https://media.geeksforgeeks.org/wp-content/uploads/20200807195934/SortedMap.png)

## Features of a TreeMap

Some important features of the treemap are as follows: 

1. This class is a member of the [Java Collections](https://www.geeksforgeeks.org/collections-in-java-2/) Framework.
2. The class implements [Map interfaces](https://www.geeksforgeeks.org/map-interface-java-examples/) including [NavigableMap](https://www.geeksforgeeks.org/navigablemap-interface-in-java-with-example/), [SortedMap](https://www.geeksforgeeks.org/sortedmap-java-examples/), and extends AbstractMap class.
3. TreeMap in Java does not allow null keys (like Map) and thus a [NullPointerException](https://www.geeksforgeeks.org/null-pointer-exception-in-java/) is thrown. However, multiple null values can be associated with different keys.
4. Entry pairs returned by the methods in this class and its views represent snapshots of mappings at the time they were produced. They do not support the [Entry.setValue](https://www.geeksforgeeks.org/map-entry-interface-java-example/)method.