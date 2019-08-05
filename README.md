# PostionSort

非比较定位排序法

>通过数组的坐标，对数字进行统计定位。

```java
/**
 * 非比较坐标定位排序，一维基本原理
 */

public class Postion {

	public static void main(String[] args) {
		Postion pv = new Postion();
		int[] arr = new int[]{1,9,120,7,884,4,99,8,8,6,100,800,7,110,12,45,87,0,1,9,539};
		List<Integer> sort = pv.sort(arr);
		for (Integer integer : sort) {
			System.out.print(integer+ " ");
		}
	}
	
	/**
	 * 定位排序
	 * @param arr
	 * @return
	 */
	public List<Integer> sort(int [] arr) {
		V1MaxAndMin mam = generateMaxAndMin(arr);
		
		int xLen = mam.max + 1;
		int[] xPostion = new int[xLen];
		
		// 写入坐标
		for (int num : arr) {
			xPostion[num] = xPostion[num] +1;
		}
		
		// 读取坐标
		List<Integer> result = new ArrayList<>();
		for(int i = 0;i<xLen;i++) {
			if(xPostion[i]>0) {
				for(int count = 0;count<xPostion[i];count++) {
					result.add(i);
				}
			}
		}
		return result;
	}
	
	/**
	 * 生成最大最小值，确定坐标范围
	 * @param arr
	 * @return
	 */
	public V1MaxAndMin generateMaxAndMin(int [] arr) {
		V1MaxAndMin mam = new V1MaxAndMin();
		mam.max = arr[0];
		mam.min = arr[0];
		for(int i=1;i<arr.length;i++) {
			if(arr[i]>mam.max) {
				mam.max = arr[i];
			} else if(arr[i]<mam.min) {
				mam.min = arr[i];
			}
		}
		return mam;
	}
	
	private static class V1MaxAndMin{
		int max;
		int min;
	}


}



```
