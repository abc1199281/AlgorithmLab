# Algorithm Lab

## Motivation: **bridge the algorithm theorem and leet code problems** 
In this repository, algorithm notes are provided to **bridge the algorithm theorem and leet code problems** [1,2].

If we only practice the leet code problems, we might be lost and frustrated due to the lack of systemetic view of algorithm.

If we only read the algorithm bible [1], we might still not be able to solve leetcode problems within a reasonable time. Because the book only provides pseudo codes which are much easier to understand/memorize and more general beyond different language. But when solving problems, there are many implementation details and variants aspects to the same algorithm. Taking Dijkstra's algorithm for example, the bible provides a pseudo code using set data structure whereas realistically we should use heap instead.

To link the algorithm theorem and leet code problems, the note contains several questions such as pseudo code from book, c++ code implementation, main idea,  limitations, complexity, etc.

The layouts of forders basically follows the outline of [1]. Besides, the experiments which are not covered in the book are located in the folder **other** or the folder with similiar chapter, but labeled with star sign. The label of the difficulty basically follows the classification of leetcode [2].

## Outline  

### Foundation
- [[Easy] Ch1 the role of algorithm in computing (22/01/03)](/Ch1_the_role_of_algorithm)  
- [[Easy] Ch3 Growth of functions (TBD)](/Ch1_the_role_of_algorithm)  
- [[Middle] Ch4 Divide and Conquer, SOP (TBD)](/Ch1_the_role_of_algorithm)  
- [[Middle] Ch4.5 Divide and Conquer, Master method (TBD)](/Ch1_the_role_of_algorithm)  

### Sorting and Order Statistics

### Data Structure
- [[TBD] Ch10 Elementary Data Structure (TBD)]
- [[TBD] Ch11 Hash Tables (TBD)]
- [[TBD] Ch12 Binary Search Trees (TBD)]
- [[TBD] Ch13 Red Black Trees (TBD)]

### Advanced Design and Analysis Techniques
- [[Middle] Ch15.3 Elementary of Dynamic Programming, SOP (22/01/03)](/Ch15_dynamic_programming/3_element_of_dynamic_programming)  

##### Graph
- [[Middle] Ch22.2 Elementary Graph Algo., BFS (22/01/01)](/Ch22_elementary_graph_algo/2_middle_breadth_first_search)  
- [[Middle] Ch22.3 Elementary Graph Algo., DFS (22/01/01)](/Ch22_elementary_graph_algo/3_middle_depth_first_search)  
- [[Middle] Ch22.4 Elementary Graph Algo., Topological Sort via DFS(22/01/01)](/Ch22_elementary_graph_algo/4_middle_topological_srot)  
- [[Middle] Ch22.* Elementary Graph Algo., Kahn's topological Sort (22/01/01)](/Ch22_elementary_graph_algo/4_middle_topological_srot)
- [[Middle] Ch23.2.1 Min. spanning tree, Kruskal (TBD)](/Ch23_min_spanning_tree/2_1_middle_Kruskal)  
- [[Middle] Ch23.2.2 Min. spanning tree, Prim (TBD)](/Ch23_min_spanning_tree/2_2_middle_Prim)  
- [[Middle] Ch24.1 Single source shortest path, Bellman-Ford (22/01/01)](/Ch24_single_source_shortest_paths/1_middle_Bellman_Ford)  
- [[Middle] Ch24.2 Single source shortest path, Directed Acyclic graph (22/01/01)](/Ch24_single_source_shortest_paths/2_middle_DirectedAcyclicGraph)  
- [[Middle] Ch24.3 Single source shortest path, Dijkstra's algorithm (22/01/01)](/Ch24_single_source_shortest_paths/3_middle_Dijkstra)  
- [[Middle] Ch24.* Single source shortest path, Shortest Path Faster Algorithm (22/01/01)](/Ch24_single_source_shortest_paths/other_middle_SPFA)  

### Hard  

## Recommendation Welcome
This is my side project to verify some algorithm concept. Recommendation to this repo is very wellcome!  
If you have any idea about this repo, just send your precious recommendation to me (poweihuang.ece06g@nctu.edu.tw). Thanks a lot.

## Recommended Book List and Reference
1. [Cormen, Thomas H., et al. Introduction to algorithms. MIT press, 2009.](https://edutechlearners.com/download/Introduction_to_algorithms-3rd%20Edition.pdf)  
As others have said, the book [1] is called the bible of Algorithm. Unless stated otherwise, the chapter number in this repository follows this book.
2. [Leet Code](https://leetcode.com/)  
This website provide very good questions.