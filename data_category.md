数据源分类是对数据的来源进行管理，通过对【不同渠道】、【不同数据接口】、【不同所属类型】的划分来规范化管理数据源。

#### 字段含义
1. 一级来源<br>
一级来源可用于表示不同数据来源的【渠道】。

2. 二级来源<br>
二级来源可用于表示同一渠道下不同的【数据接口】。

3. 所属类型<br>
所属类型用于明确该所属类型的大致划分，所属类型在数据源分类新增时确定后，后续将无法再次修改。<br>
目前共支持以下几种：
	 - 请求
	 - `Python`
	 - `HTTP`
	 - 自定义 `HTTP`
	 - 决策集
	 - 评分卡

<hr>

#### 列表
![data_category_list](./images/data_category_list.png)

#### 新增
新增所属分类为【请求】的数据源分类。<br>
<img src="./images/data_category_create_local.png" width="50%" heigh="50%" />

#### 修改
修改数据源分类时，其【所属类型】不可修改。<br>
<img src="./images/data_category_update_local.png" width="50%" heigh="50%" />

#### 详情
<img src="./images/data_category_update_local.png" width="50%" heigh="50%" />
