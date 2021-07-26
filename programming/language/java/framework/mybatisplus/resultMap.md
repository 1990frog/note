[TOC]

```
<resultMap type="com.account.web.vo.project.PExpenseVo" id="pexpenseMap">
    <collection property="checkers"  ofType="com.account.web.vo.admin.system.SysUserArchiveVo"
        select="findChecker3" column="{expenseId2=expenseId}">
    </collection>
</resultMap>
```