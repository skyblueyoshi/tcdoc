# 地图API

## 地图通用模块（MapUtils）

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:center">&#x8FD4;&#x56DE;&#x503C;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MapUtils.IsValid(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;&#x6709;&#x6548;&#xFF0C;&#x5373;&#x662F;&#x5426;&#x5728;&#x6709;&#x6548;&#x533A;&#x5757;&#x5185;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.IsAreaValid(int xi, int yi, int width, int height)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">&#x5224;&#x65AD;&#x77E9;&#x5F62;&#x533A;&#x57DF;&#x5185;&#x6240;&#x6709;&#x683C;&#x5B50;&#x662F;&#x5426;&#x90FD;&#x6709;&#x6548;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.IsSolid(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">&#x5224;&#x65AD;&#x6307;&#x5B9A;&#x683C;&#x5B50;&#x662F;&#x5426;&#x4E3A;&#x5B9E;&#x5FC3;&#x524D;&#x666F;&#x3002;
        <br
        />&#x82E5;&#x683C;&#x5B50;&#x65E0;&#x6548;&#xFF0C;&#x603B;&#x662F;&#x8FD4;&#x56DE;false&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">MapUtils.IsSolidUnsafe(int xi, int yi)</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:left">
        <p>IsSolid&#x51FD;&#x6570;&#x7684;&#x4E0D;&#x5B89;&#x5168;&#x7248;&#x672C;&#x3002;</p>
        <p>&#x683C;&#x5B50;&#x65E0;&#x6548;&#x65F6;&#x4F1A;&#x53D1;&#x751F;&#x5D29;&#x6E83;&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>



