---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Quick Sort"
subtitle: ""
summary: ""
authors: [admin]
tags: [programming, sort]
categories: []
date: 2020-02-20T09:48:14+09:00
lastmod: 2020-02-20T09:48:14+09:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

```c++
void quickSort(vector<int>& nums, int start, int end)
{
    if(start < end)
    {
        int pivot = patition(nums, start, end);
        quickSort(nums, start, pivot-1);
        quickSort(nums, pivot+1, end);
    }
}

int patition(vector<int>& nums, int start, int end)
{
    int pivot = nums[end];
    int i = start-1;
    for(int j = start; j < end; ++i)
    {
        if(nums[j] < pivot)
        {
            i++;
            swap(nums[i], nums[j]);
        }
    }
    i++;
    swap(nums[i], nums[end]);
    return i;
}
```

