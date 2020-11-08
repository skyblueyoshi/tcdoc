# 通用API

全局表名称：ut

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:center">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:center">&#x53EF;&#x7528;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">ut.positiveMod(int a, int b)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">
        <p>&#x8FD4;&#x56DE;a&#x4E0E;b&#x6C42;&#x4F59;&#x7684;&#x975E;&#x8D1F;&#x6570;&#x7ED3;&#x679C;&#x3002;</p>
        <p>&#x4F8B;1&#xFF1A;ut.positiveMod(5, 3)&#x8FD4;&#x56DE;2&#x3002;</p>
        <p>&#x4F8B;2&#xFF1A;ut.positiveMod(-5, 3)&#x8FD4;&#x56DE;1&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ut.randInt(int n)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">&#x82E5;n&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[0, n)&#x7684;&#x968F;&#x673A;&#x6574;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;0&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ut.randIntArea(int begin, int len)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">&#x82E5;len&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[begin, begin + len)&#x7684;&#x968F;&#x673A;&#x6574;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;begin&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ut.randDouble(double value)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">&#x82E5;value&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[0, value)&#x7684;&#x968F;&#x673A;&#x6D6E;&#x70B9;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;0&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ut.randDoubleArea(double begin, double len)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">&#x82E5;len&#x5927;&#x4E8E;0&#xFF0C;&#x8FD4;&#x56DE;[begin, begin + len)&#x7684;&#x968F;&#x673A;&#x6D6E;&#x70B9;&#x6570;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;begin&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ut.randSym(double value)</td>
      <td style="text-align:center">double</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">&#x8FD4;&#x56DE;(-value, value)&#x7684;&#x968F;&#x673A;&#x6D6E;&#x70B9;&#x6570;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ut.randTry(int n)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">
        <p>&#x5F53;n&#x4E3A;&#x6B63;&#x6570;&#x65F6;1/n&#x6982;&#x7387;&#x8FD4;&#x56DE;true&#xFF0C;&#x5426;&#x5219;&#x59CB;&#x7EC8;&#x8FD4;&#x56DE;false&#x3002;</p>
        <p>&#x4F8B;1&#xFF1A;ut.randTry(3)&#x6709;1/3&#x6982;&#x7387;&#x8FD4;&#x56DE;true&#x3002;</p>
        <p>&#x4F8B;2&#xFF1A;ut.randTry(2)&#x6709;&#x4E00;&#x534A;&#x6982;&#x7387;&#x8FD4;&#x56DE;true&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ut.floorDivide(int a, int b)</td>
      <td style="text-align:center">int</td>
      <td style="text-align:center">C/S</td>
      <td style="text-align:left">
        <p>&#x82E5;b&#x975E;0&#xFF0C;&#x8FD4;&#x56DE;a&#x5411;&#x4E0B;&#x53D6;&#x6574;&#x6574;&#x9664;b&#x7684;&#x7ED3;&#x679C;&#xFF0C;&#x5426;&#x5219;&#x8FD4;&#x56DE;0&#x3002;</p>
        <p>&#x4F8B;1&#xFF1A;ut.floorDivide(10, 3)&#x8FD4;&#x56DE;3&#x3002;</p>
        <p>&#x4F8B;2&#xFF1A;ut.floorDivide(-4, 3)&#x8FD4;&#x56DE;-2&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:center"></td>
      <td style="text-align:center"></td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>



