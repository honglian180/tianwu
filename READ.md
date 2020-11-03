pulic static Integer getMaxValue(List valueList){
    // List<Integer> 转 int[]
    // 想要转换成int[]类型，就得先转成IntStream。
    // 这里就通过mapToInt()把Stream<Integer>调用Integer::valueOf来转成IntStream
    // 而IntStream中默认toArray()转成int[]。
    int[] arr = list.stream().mapToInt(Integer::intValue).toArray();
    //  假设一个最大值arr[0]
    int max = arr[0];
    //  遍历数组和最值比较，得出最值
    for(int i = 1; i <arr.length; i++){
        if(arr[i] > max){
            max = arr[i];
        }
    }
    System.out.println("最大值为:" + max);
}
   原因：
   集合遍历效率较低，同时还要考虑线程安全问题
   数组遍历效率较高，不用考虑线程安全问题
   故将list集合转换为array数组来遍历求最值。
    