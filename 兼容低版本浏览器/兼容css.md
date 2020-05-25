1. Chrome中两个相邻的 a 标签中间会有空白间隙

    在父元素上加 `font-size: 0`


2. ie7 `display: inline-block` 不生效

    在 `display: inline-block` 下面加上
    ```css
        display: inline-block;
        *display: inline;
        *zoom: 1
    ```

3. ie7下设置 `vertical-align` 使用 `*vertical-align`

4. 【注意】ie7下 a 标签的颜色不会被父元素覆盖，所以a标签必须设置自己的color