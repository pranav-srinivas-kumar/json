# JSON Manipulation Header-only Library for C++

## Trivially create and manipulate JSON with one header

```cpp
#include <json.h>

int main() {
  json record;

  record["projects"]["json"]["year"] = 2017;                         // value of type integer
  record["projects"]["json"]["url"] = "https://json.org";            // value of type string
  record["projects"]["json"]["commits/day"] = 5.21;                  // value of type double
  record["projects"]["json"]["cool?"] = true;                        // value of type bool

  record["projects"]["llama"]["language"] = "C++";
  record["projects"]["llama"]["domain"] = "Linear Algebra";
  record["projects"]["llama"]["url"] = nullptr;                      // value of type null

  record["projects"]["rosmod"]["language"] = "C++/Python";
  record["projects"]["rosmod"]["url"] = "https://github.com/rosmod";
  record["projects"]["rosmod"]["active?"] = false;

  auto keys = record["projects"]["json"].keys();                     // ["year", "url", "commits/day"]
  auto query = record["projects"]["json"]["commits/day"].value();    // query = "5.21"
  
  std::string record_string = record.to_string();                    // returns a string of the json
  record.print();                                                    // pretty prints json data
  record.write("record.json");                                       // writes json to file
}
```

## Pretty JSON is pretty!

```json
{
    "projects" :
    {
        "json" :
        {
            "commits/day" : 5.21,
            "is this cool?" : true,
            "url" : "https://json.org",
            "year" : 2017
        },
        "llama" :
        {
            "domain" : "Linear Algebra",
            "language" : "C++",
            "url" : null
        },
        "rosmod" :
        {
            "active?" : false,
            "language" : "C++/Python",
            "url" : "https://github.com/rosmod"
        }
    }
}
```

## TODO

* Support for arrays
* Loading JSON from file
* Advanced search features

## LICENSE

Copyright (c) 2017 Pranav Srinivas Kumar <pranav.srinivas.kumar@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
