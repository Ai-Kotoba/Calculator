Language: [English](#English) or [����](#Chinese)
===
<span id="English">English(From google translate)</span>:
---
### Instruction manual:
- ##### Profile:
    A simple calculator developed using cpp.<br>
    The core code is located in "Calculator.h", which is used to ***calculate infix expressions in the form of strings***.<br>
    "Source.cpp" can operate on files of the specified form, but it is not important.
- ##### Scope of application:
   - OK: Decimal, Negative sign, Operator "+ - * / ( )"
   - ***NO: Positive sign***
- ##### Development environment:
   - Windows 11
   - Visual Studio 2022 Community
***
### Implementation logic:
> ##### Notice:
> ***Infix expression to postfix expression" and "Calculation of postfix expressions" are generic, 
> and the requirement changes only need to update "String parsing to infix expression"***.
- ##### Data type description:
   The program must use a special type that allows the data structure to store both operands and operators.
```cpp
struct data_type
{
	data_type(double _number);
	data_type(char _char);
	bool is_symbol;
	double number;
	char symbol;
};
```
- ##### String parsing to infix expression:
    1. '(' add infix expressions to assist in calculating postfix expressions.
    2.  Iterate over the string:
	    - Extract operands added to infix expressions, extract only positive numbers.
        - Extract operators added to infix expressions.
        - ***Handling negative signs***:
            - Identify: Consider negative signs that only appear to the right of '(' and at the beginning of a string.
            - Handling: Add 0 to the infix expression first, and then add '-' to the infix expression.
    3. ')' add infix expressions, paired with '('.
- ##### Infix expression to postfix expression:
    1.  Both postfix expressions and infix expressions are stored in queues.
    2.  Create a stack to temporarily store operators.
    3.  Iterate over the infix expression queue:
        -  If it is an operand, it is added to the postfix expression.
        -  If it is an operator(OP), compare the priority of OP and top of stack.
          	-  If the OP's priority is higher, the OP pushes the stack.
            -  Otherwise, the operator in the stack is continuously popped into the postfix expression until the priority of op is higher than the top operator on the stack. 
	    - Handling of parentheses:
           - Set the left parenthesis to the lowest precedence, but add it directly to the postfix expression.
           - If a closing parenthesis is encountered, pop the operator from the operator stack into the postfix expression until an opening parenthesis is encountered. 
    4.  If the stack is not empty, then pop the elements into the postfix expression in turn.
- ##### Calculation of postfix expressions:
    1.  Create a temporary stack for computation. 
    2.  Iterate over the postfix expression queue:
		-  If it is an operand, push it to the stack.
        -  Otherwise, remove the top two elements of the stack and perform the specified calculation.
    3.  Pop the last element on the stack to get the result.
***

<span id="Chinese">����</span>��
---
### ���:
- ##### ����:
    һ��ʹ��cpp�����ļ򵥼�������<br>
    ���Ĵ���λ��"Calculator.h"������***�����ַ�����ʽ����׺���ʽ***��<br>
    "Source.h"���Զ�ָ����ʽ���ļ����в����������ⲻ��Ҫ��
- ##### ���÷�Χ:
   - ���У�С��, ����, ������"+ - * / ( )"
   - �����У�***����***
- ##### ����������
  - Windows 11
  - Visual Studio 2022 Community
***
### ʵ���߼�:
> ##### ע��:
> ***"��׺���ʽת����׺���ʽ" �� "�����׺���ʽ" ����ͨ���ԣ� 
> ������ֻ����� "�ַ�������Ϊ��׺���ʽ"***
- ##### ������������:
  �������ʹ��һ�����ݽṹ���洢�������Ͳ�������
```cpp
struct data_type
{
	data_type(double _number);
	data_type(char _char);
	bool is_symbol;
	double number;
	char symbol;
};
```
- ##### �ַ�������Ϊ��׺���ʽ��
    1. '(' ������׺���ʽ�����������׺���ʽ��
    2. �����ַ�����
        - ��ȡ������������׺���ʽ��ֻ��ȡ������
        - ��ȡ������������׺���ʽ��
        - ***������***��
            - ʶ�𣺿��ǽ�������'('�Ҳ���ַ�����ͷ�ĸ��š�
            - ����0�ȼ�����׺���ʽ�����ź������׺���ʽ��
    3. ')' ������׺���ʽ���� '(' ��ԡ�
- ##### ��׺���ʽת����׺���ʽ��
    1. ��׺���ʽ����׺���ʽ���洢�ڶ����С�
    2. ����һ��ջ����ʱ�洢��������
    3. ������׺���ʽ�Ķ��У�
        - ����ǲ�����������ӵ���׺���ʽ�С�
        - ����ǲ�����(OP)���Ƚ�OP��ջ�������������ȼ�:
          - ��� OP �����ȼ����ߣ��� OP ѹջ��
          - ���򣬲��ϵ���ջ�еĲ���������׺���ʽ�У�ֱ�� OP �����ȼ�����ջ���Ĳ�������
        - ���ŵĴ���ʽ:
          - �������ŵ����ȼ�����Ϊ��ͣ�����ֱ����ӵ���׺���ʽ�С�
          - ������������ţ���ô�Ӳ�����ջ�в��ϵ�������������׺���ʽ�У�ֱ�����������š�
    4. ���ջ��Ϊ�գ������ν�Ԫ�ص�������׺���ʽ�С�
- ##### �����׺���ʽ��
    1. ����һ����ʱջ���ڼ��㡣
    2. ������׺���ʽ���У�
        - ����ǲ�����������ѹ��ջ��
        - ����ɾ��ջ�Ķ�������Ԫ�ز�ִ��ָ���ļ��㡣
    3. ����ջ�����һ��Ԫ�صõ������
***

### �ο�:
- ##### [PTA-7-20 ���ʽת������׺ת��׺�������ţ�������С��ת����](https://blog.csdn.net/weixin_41012699/article/details/105279523)
- ##### [C++ʵ�ּ�����������ջ�������׺���ʽ���и�����С������](https://www.whcsrl.com/blog/1029875)
