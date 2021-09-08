### from anytree import Node
**from collections import deque**

tree_deque = deque() #non capisco perchè se creo la queue fuori dalla funzione, il risultato è corretto, altrimenti no

def breadth_first_visit(root_node):
    result = list()
    
    if root_node.name not in result:
        result.append(root_node.name)

    if root_node.children != ():
        for child in root_node.children:
            tree_deque.append(child)

    while len(tree_deque) > 0:
        result.extend(breadth_first_visit(tree_deque.popleft()))

    return result



book = Node("book")
chapter_1 = Node("chapter1", book)
chapter_2 = Node("chapter2", book)
paragraph_1 = Node("paragraph1", chapter_1)
text_1 = Node("text1", paragraph_1)
quotation_1 = Node("quotation1", paragraph_1)
text_2 = Node("text2", quotation_1)
text_3 = Node("text3", paragraph_1)
quotation_2 = Node("quotation2", paragraph_1)
text_4 = Node("text4", quotation_2)
paragraph_2 = Node("paragraph2", chapter_1)
text_5 = Node("text5", paragraph_2)
paragraph_3 = Node("paragraph3", chapter_1)
text_6 = Node("text6", paragraph_3)
text_7 = Node("text7", chapter_2)
text_8 = Node("text8", book)
bfv = [book,
       chapter_1, chapter_2, text_8,
       paragraph_1, paragraph_2, paragraph_3, text_7,
       text_1, quotation_1, text_3, quotation_2, text_5, text_6,
       text_2, text_4]
print(breadth_first_visit(book))
