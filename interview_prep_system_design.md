# System design

## Hashing and Consistent hashing
Link: [https://www.youtube.com/watch?v=bBK_So1u9ew](https://www.youtube.com/watch?v=bBK_So1u9ew)

Hashing is a way to retrieve the value very fast.

What we need for this:
1. Key value pairing
2. Hashing function
3. Hash Table

Since the hashing function can bring out very large values, you do a very simple thing.
The position in hash table will be `hashed-val % num_buckets`.

### Collisions
1. One way to do is to use linked list reference into the bucket in key value pair. Hence do chaining. Save the key as well. So go to the hash table, if there is a linked list, iterate over the linked list until you find the key.
2. You can go and look for the next available location and save it there.

### Problem with the normal hashing solution
Let's say a key gives a hash as `91192` and we had 10 buckets. This mudulo operation to find where it needs to go will map it to bucket `#2` which is the third bucket.
Now let's assume that out of the 10  buckets, 7 were held by computer #1 and the other 3 were held by computer #2. If the availability of computer #2 is no longer available, the following issues arise:
1. Where will you store the data which had the hashed pointing to the bucket held by computer #2.
2. If the available buckets is reduced from 10 to 7, the resulting change in the bucket ID post the modulo operation will make the system go haywire

### Consistent hashing
Instead of earlier hash tables which look like this:
```
+---+-----+
|Key|Value|
+---+-----+
| 0 | --  |
| 1 | --  |
| 2 | --  |
   ...
| 9 | --  |
+---+-----+
```
you now have random numbers as keys (in ascending order):

```
+-----+-----+
|Key  |Value|
+-----+-----+
| 10  | --  |
| 21  | --  |
| 221 | --  |
   ...
| 990 | --  |
+-----+-----+
```
With this, you find the bucket by finding the hash and then finding the first key in the hash table which is just greater than your hash value.

Hence if your hash is `200`, you will land into the bucket `221`.

What happens if the key `990` fails or you have to add `1001` hash in the table? 
Well, in that case, since the last number will be `990`, you revert back to the first entry which is `10` and add your value there.
If `990` fails, only the bucket values that were saved in `990` are no longer accessible. Any lookup for anything else does not die. Also, if any addition needs to happen which earlier would have gone to bucket with key `990` would now go to `10`, hence a remap.

## Netflix system architecture
Netflix operates in two clouds:
1. Amazon AWS: Anything relating to bookkeeping
2. OpenConnect: Anything related to content delivery

Three important components:
1. OpenConnect 
2. Backend
3. Client

Openconnect is Netflix's own CDN (Content delivery network) - servers placed in different locations all over the world.

System

