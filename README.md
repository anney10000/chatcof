# How to use
Download and install Anconda

In the chatcof folder of the Jupyter Lab interface, create a notebook file

Then on the first line, type:
```
%run database.py
```
This step is to have Jupyter run our COF querier and load the run function into memory so that it can be called at any time later

You can then run the run function on the second line to get the corresponding COF composition

## Usage examples

The program supports two star display methods (for example, the current maximum of 5 is displayed)

**1. Get the synthesis scheme of TALB and display the star rating in the first mode**

```jupyter
run("tapb", sort=1)
```

In fixed display 5-1★★, the order of the synthesis protocol is sorted by the similarity between the corresponding compound name and the user-specified compound name

**2. Get the synthesis scheme of TAB and display the star rating in the second mode**

```jupyter
run("tapb")
# Or
run("tapb", sort=2)
```

According to the similarity between the corresponding compound name and the compound name specified by the user, a scoring mechanism is formulated, and the higher the similarity, the higher the star rating

The scoring mechanism is as follows:

1. ★★★★★ - Number of characters from target compound = 0
2. ★★★★ ☆- Number of characters from the target compound < = 3
3. ★★★ ☆☆- Number of characters different from the target compound < = 6
4. ★★ ☆☆☆- Number of characters from the target compound < = 9
5. ★ ☆☆☆☆- Number of characters from the target compound > 9

At present, the program defaults to the second mode

**3.Search for synthesis protocols based on temperature and time conditions**

```jupyter
# Search for a synthesis protocol at a specific temperature
run("120℃")

# Search for a composition scheme at a specific time
run("72h") # Search by hour
run("3 days") # Search by number of days

# Combine search temperature and time conditions
run("120°C 72h") # Search for a synthesis protocol at 120°C and 72 h simultaneously
```

Formats supported by search criteria:
- Temperature: Support °C, °C, C and other formats, such as: 120°C, 120°C, 120C
-Time:
  - Hours: Supports h, hour, and hours formats, for example: 72h and 72 hours
  - Days: The format of day and days is supported, for example, 3 days and 3d

All search results support two star display modes:
1. sort=1: fixed display from 5★ to 1★
2. sort=2 (default): Displays the star rating based on the match
  - ★★★★★: Exact match
  - ★★★★ ☆:The number of characters in phase difference ≤ 3
  - ★★★ ☆☆: The number of characters in phase difference ≤ 6
  - ★★ ☆☆☆: The number of characters in phase difference ≤ 9
  - ★ ☆☆☆☆: The number of characters in phase difference > 9

If no relevant synthesis protocol is found, the program prompts you to visit Web of Science to search for relevant documents.
