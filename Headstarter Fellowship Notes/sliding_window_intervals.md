# Sliding Window & Intervals

### Optimize Event Schedule Problem
Time: 40 minutes
```python
# Given a schedule of events represented as an array of intervals, where each interval is described by a pair [start, end] indicating the event's start and end time, design a strategy to minimize the number of events that need to be canceled to ensure no events overlap.
# Each event is distinct, and overlapping is defined as two events having any common time between them (excluding the end of one event and the start of another).
# Provide the minimum number of events that must be canceled to achieve a non-overlapping schedule.

# Example 1:
# Input: intervals = [[1,2],[2,3],[3,4],[1,3]]
# Output: 1
# Explanation: Canceling the event [1,3] ensures the remaining events do not overlap.

# Example 2:
# Input: intervals = [[1,2],[1,2],[1,2]]
# Output: 2
# Explanation: Canceling two [1,2] events ensures the remaining schedule is non-overlapping.

# Example 3:
# Input: intervals = [[1,2],[2,3]]
# Output: 0
# Explanation: The schedule is already non-overlapping, so no events need to be canceled.

# Constraints:
# 1 <= intervals.length <= 10^5
# intervals[i].length == 2
# -5 * 10^4 <= start < end <= 5 * 10^4

def optimizeEventSchedule(intervals):
```

###
