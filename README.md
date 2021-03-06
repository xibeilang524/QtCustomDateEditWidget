

# QtCustomDateEdit

I used **cpp** to build a custom dateEdit widget class in **Qt**. 

## Development Environment

* Qt5.12.1

* MinGW 7.3.0 64-bit(Windows10)

## Example

### How to use

```c++
    #include "customdateedit.h"
```

### Create Widget

![CustomDateEdit][customDateEdit]

```c++
    CustomDateEdit * customDateEdit = new CustomDateEdit(this); // 创建自定义日期编辑控件
    QHBoxLayout * hBoxLayout = new QHBoxLayout(); // 创建水平布局

    hBoxLayout->addWidget(customDateEdit); // 通过布局添加自定义日期编辑控件
    ui->centralWidget->setLayout(hBoxLayout); // 设置布局
```

### Change Calendar Type

![ChangeType][changeType]

```c++
    CustomDateEdit * customDateEdit = new CustomDateEdit(this); // 默认是天数型的日历
    CustomDateEdit * customDateEdit_1 = new CustomDateEdit(this, CustomDateEdit::MONTH); // 月份日历
    CustomDateEdit * customDateEdit_2 = new CustomDateEdit(this, CustomDateEdit::YEAR); // 年份日历
    QHBoxLayout * hBoxLayout = new QHBoxLayout();

    QPushButton * changeDayButton = new QPushButton(this); // 创建选择天数型日历的按钮
    changeDayButton->setText("day");
    changeDayButton->setStyleSheet("background: white; color: black;");

    QPushButton * changeMonthButton = new QPushButton(this); // 创建选择月份型日历的按钮
    changeMonthButton->setText("month");
    changeMonthButton->setStyleSheet("background: white; color: black;");

    QPushButton * changeYearButton = new QPushButton(this); // 创建选择年份型日历的按钮
    changeYearButton->setText("year");
    changeYearButton->setStyleSheet("background: white; color: black;");

    hBoxLayout->addWidget(customDateEdit);
    hBoxLayout->addWidget(customDateEdit_1);
    hBoxLayout->addWidget(customDateEdit_2);

    hBoxLayout->addWidget(changeDayButton);
    hBoxLayout->addWidget(changeMonthButton);
    hBoxLayout->addWidget(changeYearButton);

    connect(changeDayButton, &QPushButton::clicked, this, [=]() {
        customDateEdit_2->changeType(CustomDateEdit::DAY);
    }); // 点击天数按钮选择天数型日历的信号槽
    connect(changeMonthButton, &QPushButton::clicked, this, [=]() {
        customDateEdit_2->changeType(CustomDateEdit::MONTH);
    }); // 点击月份按钮选择月份型日历的信号槽
    connect(changeYearButton, &QPushButton::clicked, this, [=]() {
        customDateEdit_2->changeType(CustomDateEdit::YEAR);
    }); // 点击年份按钮选择年份型日历的信号槽

    ui->centralWidget->setLayout(hBoxLayout);
```

[customDateEdit]: README/customDateEdit.gif
[changeType]: README/customDateEdit_changeCalendarType.gif
