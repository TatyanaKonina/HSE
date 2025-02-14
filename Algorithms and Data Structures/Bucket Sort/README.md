# Bucket Sort
Задача: Реализовать алгоритм блочной/карманной сортировки (bucket sort).

Предполагаем, что интервал (min;max) наших значений разбит на 2*n корзин (где n - число элементов во входном массиве) равного размера. Данную логику можно реализовать несколькими путями, конкретной формулы не дано, подумайте сами. На рисунке b_len - длина интервала одной корзины. При этом важно, что числа min + b_len, min + b_len * 2, min + b_len * 3 и так далее не должны входить в те интервалы, для которых они являются правой границе (точки на графике "выколоты").
 То есть min + b_len - относится к корзине 1 (не 0), min + b_len*2 - к корзине 2 (не к корзине 1) и так далее. Последний элемент max должен относиться к последней корзине, обратите на это внимание.
 
 Входные данные: количество элементов массива, далее сам массив неотрицательных вещественных чисел. Каждое число имеет как минимум один знак после точки (целые числа записываются как x.0, где х - целая часть).
 
 Результат: необходимо вывести подробные лог работы алгоритма (см. пример).
 
 ####Sample Input:
 
 10
 0.50 100.00 99.97 51.20 53.90 28.10 25.50 66.40 65.70 0.00 
 ####Sample Output:
 
 ####Initial array:
 0.50 100.00 99.97 51.20 53.90 28.10 25.50 66.40 65.70 0.00 
 
 #####Bucket:
 0.50 0.00 
 #####Sorted bucket:
 0.00 0.50 
 
 #####Bucket:
 28.10 25.50 
 #####Sorted bucket:
 25.50 28.10 
 
 #####Bucket:
 51.20 53.90 
 #####Sorted bucket:
 51.20 53.90 
 
 #####Bucket:
 66.40 65.70 
 #####Sorted bucket:
 65.70 66.40 
 
 #####Bucket:
 100.00 99.97 
#####Sorted bucket:
 99.97 100.00 
 
 ####Final array:
 0.00 0.50 25.50 28.10 51.20 53.90 65.70 66.40 99.97 100.00 