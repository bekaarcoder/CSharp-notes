## Find the occurance of each word in a string

```cs
public static void Main(string[] args)
{
    string str = "I am learning learning C C C Sharp Sharp programming";
    Dictionary<string, int> dict = new Dictionary<string, int>();

    int count = 1;
    string[] arr = str.Split(' ');

    for(int i = 0; i < arr.Length; i++)
    {
        if(!dict.ContainsKey(arr[i]))
        {
            dict.Add(arr[i], count);
        } else
        {
            int oldCount = dict[arr[i]];
            dict[arr[i]] = oldCount + 1;

        }
    }

    foreach(KeyValuePair<string, int> word in dict)
    {
        Console.WriteLine("Occurance of {0} is {1}", word.Key, word.Value);
    }

    Console.ReadLine();
}
```
