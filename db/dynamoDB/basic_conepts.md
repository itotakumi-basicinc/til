## How it works

- Data is located based on a key known as the Partition Key, which makes DynamoDB fast at fetching data.  
- DynamoDB doesn’t use an offset system; instead, it uses a cursor-based approach. So, if the system needs to fetch page=5 with limit=10, it has to scan from the beginning.  
- DynamoDB evaluates the limit before applying filter conditions, which means it’s impossible to always get the exact number of items specified by the limit.
