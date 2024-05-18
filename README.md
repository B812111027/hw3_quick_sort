#include <iostream>
#include <vector>

// 函數：交換兩個數值
void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

// 函數：分割數組並返回樞紐位置
int partition(std::vector<int> &arr, int low, int high) {
    int pivot = arr[high]; // 選擇最右邊的元素作為樞紐
    int i = low - 1; // i 是比樞紐小的元素的索引

    for (int j = low; j < high; j++) {
        // 如果當前元素小於或等於樞紐
        if (arr[j] <= pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    // 把樞紐元素放到正確的位置
    swap(arr[i + 1], arr[high]);
    return i + 1; // 返回樞紐位置
}

// 函數：快速排序的主函數
void quickSort(std::vector<int> &arr, int low, int high) {
    if (low < high) {
        // p 是分割點，arr[p] 已經排好序
        int p = partition(arr, low, high);

        // 遞歸地對樞紐左邊和右邊的數列進行排序
        quickSort(arr, low, p - 1);
        quickSort(arr, p + 1, high);
    }
}

int main() {
    // 初始化數組
    std::vector<int> arr = {10, 7, 8, 9, 1, 5};

    // 輸出未排序的數組
    std::cout << "未排序數組: ";
    for (int i : arr) {
        std::cout << i << " ";
    }
    std::cout << std::endl;

    // 進行快速排序
    quickSort(arr, 0, arr.size() - 1);

    // 輸出已排序的數組
    std::cout << "已排序數組: ";
    for (int i : arr) {
        std::cout << i << " ";
    }
    std::cout << std::endl;

    return 0;
}
//try out 
