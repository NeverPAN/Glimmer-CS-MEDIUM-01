# CS-MEDIUM-01
## part 1
#### ΪʲôҪʹ���ַ���������ʾ������
����λ��������ͨ�����������ܴ���ͱ��ķ�Χ
#### ��δ�����������еĽ�λ�ͽ�λ���⣿
����ʹ����һ������plus���������λ�ͽ�λ
#### ��δ�����
������ȡ���ţ���������ʽ����

![Alt text](image1.png) 
       
     #include <stdio.h>  
     #include <stdlib.h>  
     #include <string.h>  

    #define MAX_SIZE 128


    int main() {
    char str1[MAX_SIZE];
    char str2[MAX_SIZE];
    printf("�������һ��������");
   
        printf("%s",str1);
        return 0;
        }

### step2 ʵ�ִ����ӷ�
   ![Alt text](2.png)  

    #include <stdio.h>  
    #include <stdlib.h>  
    #include <string.h>  


    #define MAX_SIZE 100


    // maxer���� �ж�str1 �Ƿ����str2
    int maxer(char* str1, char* str2)
    {
        int len1 = strlen(str1);
        int len2 = strlen(str2);
    if (len1 > len2)
        return 1;
    else if (len1 < len2)
        return -1;
    else
    {
        int n = strcmp(str1, str2);
        if (n > 0)
            return 1;
        else if (n == 0)
            return 0;
        else if (n < 0)
            return -1;
    }
    }

    //  �ӷ�����
    char* add(char* str1, char* str2)
    {
    //  ȷ���ϴ󣬽�С���ַ���������ȡ���ǵĳ���
    int n = maxer(str1, str2);
    char* max_str = n >= 0 ? str1 : str2;
    char* min_str = n >= 0 ? str2 : str1;
    int len_max = strlen(max_str);
    int len_min = strlen(min_str);

    //  ���� �ϴ��ַ��� ���ȴ�1 �Ŀռ� �洢���
    char* str =(char*)malloc((MAX_SIZE + 1)*sizeof(char));
    str[len_max + 1] = '\0'; //����������������������ᳬ�������Ǹ�����1λ���λ��
    


    //  ���мӷ�����
    int plus = 0;        // plus Ϊ ��λ
    int i = len_max - 1; // ��� �ϴ��ַ��� ���λ�ַ���λ�ã������0����Ҫ��1��
    int j = len_min - 1; // ��� ��С�ַ��� ���λ�ַ���λ��
    for (; i >= 0; i--)
    {
        if (j >= 0)         //ֱ����С�ַ�������֮ǰ
        {
            str[i + 1] = max_str[i] + min_str[j] - '0' + plus; // �ַ���ӣ�λ������ 1
            j--;                                               // ��С����λ����ǰ(i--�ϴ�����λ����ǰ)
            plus = str[i + 1] > '9' ? 1 : 0;                   // �ж��Ƿ��λ�����������������λ�����ᳬ��1��
            if (plus == 1)
                str[i + 1] -= 10; // ��λ ��� 10
        }
        else // ��С�ַ������ַ� ȫ������
        {
            str[i + 1] = max_str[i] + plus;    //ͬ��ֻ�ǲ��ڼӽ�С����
            plus = str[i + 1] > '9' ? 1 : 0;
            if (plus == 1)
                str[i + 1] -= 10;
        }
    }

    //  ���� ���λ �Ƿ� ��λ��ȷ�� ����ָ��
    if (plus == 0)
        return str + 1; // ���� str ����1λ��λ��
    else
    {
        str[0] = '1'; // str��λ �� '1'
        return str;   // ���� str
    }
    }

    int main() {
    char str1[MAX_SIZE];
    char str2[MAX_SIZE];
    char operation;

    printf("�������һ��������");
    if (scanf_s("%s", str1, MAX_SIZE) != 1) {
        printf("�������\n");
        return 1;
    }
    printf("������ڶ���������");
    
    if (scanf_s("%s", str2, MAX_SIZE) != 1) {
        printf("�������\n");
        return 1;
    }
    printf("���������(A,��ʾ�ӷ�,M,��ʾ����,X��ʾ�˷�,D��ʾ��������");
    getchar();
    scanf_s("%c", &operation);

    char* result;
    if (operation == 'A') {
        result = add(str1, str2);
    }
     printf("���Ϊ��%s\n", result);

    // ע���ͷŶ�̬������ڴ�
    free(result);

    return 0;
}

## part 4 ��װ��������
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>


    #define MAX_SIZE 100


    // maxer���� �ж�str1 �Ƿ����str2
    int maxer(char* str1, char* str2)   
    {
    int len1 = strlen(str1);
    int len2 = strlen(str2);
    if (len1 > len2)
        return 1;
    else if (len1 < len2)
        return -1;
    else
    {
        int n = strcmp(str1, str2);
        if (n > 0)
            return 1;
        else if (n == 0)
            return 0;
        else if (n < 0)
            return -1;
    }
    }

    //  �ӷ�����
    char* add(char* str1, char* str2)
    {
    //  ȷ���ϴ󣬽�С���ַ���������ȡ���ǵĳ���
    int n = maxer(str1, str2);
    char* max_str = n >= 0 ? str1 : str2;
    char* min_str = n >= 0 ? str2 : str1;
    int len_max = strlen(max_str);
    int len_min = strlen(min_str);

    //  ���� �ϴ��ַ��� ���ȴ�1 �Ŀռ� �洢���
    char* str =(char*)malloc((MAX_SIZE + 1)*sizeof(char));
    str[len_max + 1] = '\0'; //����������������������ᳬ�������Ǹ�����1λ���λ��
    


    //  ���мӷ�����
    int plus = 0;        // plus Ϊ ��λ
    int i = len_max - 1; // ��� �ϴ��ַ��� ���λ�ַ���λ�ã������0����Ҫ��1��
    int j = len_min - 1; // ��� ��С�ַ��� ���λ�ַ���λ��
    for (; i >= 0; i--)
    {
        if (j >= 0)         //ֱ����С�ַ�������֮ǰ
        {
            str[i + 1] = max_str[i] + min_str[j] - '0' + plus; // �ַ���ӣ�λ������ 1
            j--;                                               // ��С����λ����ǰ(i--�ϴ�����λ����ǰ)
            plus = str[i + 1] > '9' ? 1 : 0;                   // �ж��Ƿ��λ�����������������λ�����ᳬ��1��
            if (plus == 1)
                str[i + 1] -= 10; // ��λ ��� 10
        }
        else // ��С�ַ������ַ� ȫ������
        {
            str[i + 1] = max_str[i] + plus;    //ͬ��ֻ�ǲ��ڼӽ�С����
            plus = str[i + 1] > '9' ? 1 : 0;
            if (plus == 1)
                str[i + 1] -= 10;
        }
    }

    //  ���� ���λ �Ƿ� ��λ��ȷ�� ����ָ��
    if (plus == 0)
        return str + 1; // ���� str ����1λ��λ��
    else
    {
        str[0] = '1'; // str��λ �� '1'
        return str;   // ���� str
    }
    }

    //��������
    char* minus(char* str1, char* str2)
    {
    //  ȷ����� ���� �� 0����Ϊ1������Ϊ-1�򸺣�str1��ʾ��������str2��ʾ������
    int  is_neg = maxer(str1, str2);

    if (is_neg == 0)
        return "0"; // ��Ϊ 0, ֱ�ӷ��� "0" ����

    char* max_str = is_neg > 0 ? str1 : str2;
    char* min_str = is_neg > 0 ? str2 : str1;
    int len_max = strlen(max_str);
    int len_min = strlen(min_str);

    char* str =(char*)malloc((MAX_SIZE + 1)*sizeof(char));
    str[len_max + 1] = '\0';
    


    //  ���м�������
    int plus = 0; // plus Ϊ��λ
    int i = len_max - 1;
    int j = len_min - 1;    //��ӷ����ƣ������λ��ʼ��
    for (; i >= 0; i--)
    {
        if (j >= 0)
        {
            str[i + 1] = max_str[i] - min_str[j] + '0' + plus; // �ַ��������0�������ַ�
            j--;
            plus = str[i + 1] < '0' ? -1 : 0; // �Ƿ� ��λ
            if (plus == -1)
                str[i + 1] += 10; // ��λ ��� 10
        }
        else
        {
            str[i + 1] = max_str[i] + plus;
            plus = str[i + 1] < '0' ? -1 : 0;
            if (plus == -1)
                str[i + 1] += 10;
        }
    }

    //  ȷ�����һ�� ǰλ0 ��λ�ã�Ĭ�� str��λ Ϊ'0'����Ϊ�������ͳһ�ѽ�����ƶ���һλ
    int n_zero = 0;
    for (int i = 1; i <= len_max; i++)
    {
        if (str[i] != '0')
            break;
        n_zero++;            //��������0��λ�õ�ʱ��i=n_zero����Ϊ��ʱn_zero��ִ��
                             //���һ�֣���ִ���˵�ÿһ��n_zero����i��++
    }

    //  ���� ���� �� ���һ��ǰλ0��λ�� ȷ�� ����ָ��
    if (is_neg < 0)
    {
        str[n_zero] = '-';   // �����һ��ǰ��0�� ��Ϊ '-'�����ƶ�һλ��str[n_zero] ��Ϊ��Ҫλ����
        return str + n_zero; // ����'-'��λ�ã���n_zero=2��str+n_zero��Ӧ����str�ַ�����ӵ������ַ���ͷ������
    }                         //����Ϊ����ĳ���ͳһ�����������ƶ���һλ��������str+n_zero��Ϊ��Ҫ��

    else
        return str + n_zero + 1; // �������һ��ǰ��0 ����1λ��λ��
}

    //�˷�����
    char* mult(char* str1, char* str2)
    {
    // �ж� str1 �� str2 ���Ƿ�Ϊ 0,����, ���� "0" ����
    if (*str1 == '0' || *str2 == '0')
        return "0";

    // �Խ�С��ѭ��������ѭ�����������Ч��
    int n = maxer(str1, str2);
    char* max_str = n > 0 ? str1 : str2;
    char* min_str = n > 0 ? str2 : str1;
    int len_min = strlen(min_str);

    // ���г˷�����
    char* str_sum = "0";
    // str2ÿ���ַ���str1
    for (int i = 0; i < len_min; i++)
    {
        char* str = "0";  
        int m = (int)(min_str[i] - '0'); // ���ַ�ת������
        if (m == 0)
            continue;
        else
        {
            for (int j = 0; j < m; j++)
                str = add(str, max_str);
        }
        // �����ַ�λ�� ��str������ '0'
        int len = strlen(str);
        for (int j = 0; j < len_min - i - 1; j++)   //����6666*6666,6666*6000����6666�Լ�6������ٲ�3��0��4-0-1=3
        {
            str[len + j] = '0';
        }
        str[len + len_min - i - 1] = '\0';            
        //printf("%s\n", str);
        // ��ÿ�εõ��Ľ�����
        str_sum = add(str_sum, str);
        //printf("%s\n", str_sum);
    }
    return str_sum;
}
    // ��������
    char* divi(char* str1, char* str2)
    {
    // ���һЩ�������
    if (*str2 == '0')
        return " 0 ������Ϊ������";
    if (maxer(str1, str2) == -1)   
        return "0";

    // ��ʼ�� ���������������������ͽ��
    char* str_mol = add(str1, "0");  // �õ� str1 �������ں����ĳ�����������У�����ֱ���޸�ԭʼ�ı�����str1������ȷ��ԭʼ���ݵ�������
    char* str_divi = add(str2, "0"); // �õ� str2 ����
    char* str_sum = "0";

    // ���г�������
    int n = strlen(str1) - strlen(str2); //��str1�� str2 ���룬����¼�ƶ�λ�� n(��0�ĸ���)
    char* str_n = "1";
    for (int i = 0; i < n; i++)
        str_n = mult(str_n, "10");    // �õ�str_divi ����ı���,��Ҳ������ĺ���
    str_divi = mult(str_divi, str_n); // ʵ���Ҷ���

    for (int i = 0; i <= n; i++)
    {
        while (maxer(str_mol, str_divi) >= 0) //˵��str_mol������һֱ�����ʱ�򣬶�����ִ�м�������
        {
            str_mol = minus(str_mol, str_divi);
            str_sum = add(str_sum, str_n); // ��ÿ�ν��������
        }
        if (i < n)
            *(str_n + strlen(str_n) - 1) = '\0';       // ����ȥ��βλ�õ� '0'
            *(str_divi + strlen(str_divi) - 1) = '\0'; // ����ȥ��βλ�õ� '0'
        
    }
    return str_sum;
    }

    int main() {
    char str1[MAX_SIZE];
    char str2[MAX_SIZE];
    char operation;

    printf("�������һ��������");
    if (scanf_s("%s", str1, MAX_SIZE) != 1) {
        printf("�������\n");
        return 1;
    }
    printf("������ڶ���������");
    
    if (scanf_s("%s", str2, MAX_SIZE) != 1) {
        printf("�������\n");
        return 1;
    }
    printf("���������(A,��ʾ�ӷ�,M,��ʾ����,X��ʾ�˷�,D��ʾ��������");
    getchar();
    scanf_s("%c", &operation);

    char* result;
    if (operation == 'A') {
        result = add(str1, str2);
    }
    else if (operation == 'M') {
        result = minus(str1, str2);
    }
    else if (operation == 'X') {
        result = mult(str1, str2);
    }
    else if (operation == 'D') {
        result = divi(str1, str2);
    }
    else {
        printf("��Ч������\n");
        return 1;
    }

    printf("���Ϊ��%s\n", result);

    // ע���ͷŶ�̬������ڴ�
    free(result);

    return 0;
    }
![Alt text](3.png)  
![Alt text](4.png)  
![Alt text](5.png)  