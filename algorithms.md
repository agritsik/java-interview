1. Сортировка пузырьком
1. Сортировка вставками
1. Быстрая сортировка
1. Сортировка слиянием

## 1. Сортировка пузырьком

*Сортировка пузырьком (bubble sort)*

**Сложность - O(n^2)**

```java
int[] arr = new int[]{9, 2, 5, 1, 0, -15, 25, 16, -6, 21};

    private void bubbleSorting() {

        for (int i = arr.length -1; i > 0; i--) {

            for (int j = 0; j < i; j++) {

                if (arr[j] > arr[j+1]) {
                    int tmp = arr[j+1];
                    arr[j+1] = arr[j];
                    arr[j] = tmp;
                }

            }

        }

    }
```

## 2. Сортировка выбором

*Сортировка выбором (selection sort)*

**Сложность - O(n^2)**

```java
private void selectionSort() {

    for (int i = 0; i < arr.length; i++) {

        int minIndex = i;
        int minElement = arr[i];

        for (int j = i; j < arr.length; j++) {
            if (arr[j] < minElement) {
                minIndex = j;
                minElement = arr[j];
            }
        }

        if (minIndex != i) {
            arr[minIndex] = arr[i];
            arr[i] = minElement;
        }

    }

}
```

## 3. Быстрая сортировка

*Быстрая сортировка (quick sort)*

**Сложность - O(n*log(n)), в худшем случае - O(n^2)**

Алгоритм сортировки:

1. Выбрать опорный элемент(pivot) из массива. Опорным элементом может быть любой элемент,
в том числе первый или последний, но лучше выбрать средний элемент.
2. Отсортировать массив таким образом, чтобы все элементы, значение которых меньше опорного элемента,
были слева от него, а все элементы, которые больше опорного - справа.
3. Рекурсивно применить 1 и 2 шаг к полученным подмассивам.

```java
public class MyQuickSort {

    private int array[];
    private int length;

    public void sort(int[] inputArr) {

        if (inputArr == null || inputArr.length == 0) {
            return;
        }
        this.array = inputArr;
        length = inputArr.length;
        quickSort(0, length - 1);
    }

    private void quickSort(int lowerIndex, int higherIndex) {

        int i = lowerIndex;
        int j = higherIndex;
        // calculate pivot number, I am taking pivot as middle index number
        int pivot = array[lowerIndex+(higherIndex-lowerIndex)/2];
        // Divide into two arrays
        while (i <= j) {
            /**
             * In each iteration, we will identify a number from left side which
             * is greater then the pivot value, and also we will identify a number
             * from right side which is less then the pivot value. Once the search
             * is done, then we exchange both numbers.
             */
            while (array[i] < pivot) {
                i++;
            }
            while (array[j] > pivot) {
                j--;
            }
            if (i <= j) {
                exchangeNumbers(i, j);
                //move index to next position on both sides
                i++;
                j--;
            }
        }
        // call quickSort() method recursively
        if (lowerIndex < j)
            quickSort(lowerIndex, j);
        if (i < higherIndex)
            quickSort(i, higherIndex);
    }

    private void exchangeNumbers(int i, int j) {
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }

    public static void main(String a[]){

        MyQuickSort sorter = new MyQuickSort();
        int[] input = {24, 2, 45, 20, 56, 75, 2, 56, 99, 53, 12};
        sorter.sort(input);
        for(int i:input){
            System.out.print(i + " ");
        }
    }
}
```

## 3. Быстрая сортировка

*Сортировка слиянием (merge sort)*

```java
private static int[] merge(int[] arr_1, int[] arr_2) {

	int len_1 = arr_1.length, len_2 = arr_2.length;
	int a = 0, b = 0, len = len_1 + len_2; // a, b - счетчики в массивах
	int[] result = new int[len];

	for (int i = 0; i < len; i++) {
		if (b < len_2 && a < len_1) {
			if (arr_1[a] > arr_2[b]) result[i] = arr_2[b++];
			else result[i] = arr_1[a++];
		} else if (b < len_2) {
			result[i] = arr_2[b++];
		} else {
			result[i] = arr_1[a++];
		}
	}

	return result;

}
```
