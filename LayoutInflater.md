#### LayoutInflater

* 作用：把xml类型的布局转化成相应的View对象

  1. LayoutInflater inflater = getLayoutInflater(); //调用Activity的getLayoutInflater()
  2. LayoutInflater inflater = LayoutInflater.from(context);
  3. LayoutInflater localinflater =(LayoutInflater)context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);

* inflater.inflater

  * ```java
    inflate(int resource, ViewGroup root, boolean attachToRoot)
    ```

  * ```java
    inflate(int resource, ViewGroup root)//attachToRoot = true
    ```

  * If attachToRoot is set to true, then the layout file specified in the first parameter is inflated and attached to the ViewGroup specified in the second parameter.

    * view对象将直接绑定到ViewGroup

  * When attachToRoot is false, the layout file from the first parameter is inflated and returned as a View. 

    * view对象将被填充，但是不会绑定到ViewGroup上，需要手动addView()绑定View

  * attachToRoot 必须设置为 false的情况

    * recyclerview  

      * ```java
        public ViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
            LayoutInflater inflater = LayoutInflater.from(getActivity());
            View view = inflater.inflate(android.R.layout.list_item_recyclerView, parent, false);
            return new ViewHolder(view);
        }
        ```

      * 由于recyclerview会负责填充和绑带viewholder

    * Fragment

      * 由于FragmentManager负责add, remove and replace Fragments

* 参考 https://www.bignerdranch.com/blog/understanding-androids-layoutinflater-inflate/

  ​