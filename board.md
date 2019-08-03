def binary(arr, target)
    return [] if arr.empty?
    half = arr.length / 2
    lt_arr = arr.take(half)
    rt_arr = arr.drop(half)

    if target == rt_arr.first
        return rt_arr[half]
    elsif target == lt_arr.last
        return lt_arr[half]
    else
        binary((lt_arr[0..-2] + rt_arr[1..-1]),target)
    end

    case target <=> arr[half]
    when -1
        binary(lt_arr, target)

end


, 9

|1| 7|

 9| 16| 42| == 9


 [7 9 1 42 16].merge_sort
    [7, 9, 1]

class Array

    def merge_sort(&prc)
    return self if length == 1

    mid = length / 2

    left = self.take(mid) [1, 7, 9] --- [7, 9] l , [1] r
    right = self.drop(mid) [16, 42]

    left_sorted = left.merge_sort(&prc)
    right_sorted = right.merge_sort(&prc)

    Array.merge(left_sorted, right_sorted, prc)
    end


    def merge(left, right, prc)
        merge_arr = []
        prc ||= Proc.new { |a, b| a <=> b }

        until left.empty? || right.empty?
            if prc.call(left.first, right.first) == -1
                merge_arr << left.shift
            else
                merge_arr << right.shift
            end
        end

        merge_arr + left + right
    end

    [1, 7, 9, 16, 42]
end

class Array
    def my_each(&block)
        i = 0
        while i < self.length
            block.call(self[i])
            i += 1
        end
        self
    end
end

# Without an argument:
[["a"], "b", ["c", "d", ["e"]]].my_flatten = ["a", "b", "c", "d", "e"]

# When given 1 as an argument:
# (Flattens the first level of nested arrays but no deeper)
[["a"], "b", ["c", "d", ["e"]]].my_flatten(1) = ["a", "b", "c", "d", ["e"]]

class Array
    def my_flatten(value)
        return self if self.empty? || value < 0
        new_arr = []
        self.each do |el|
            if el.is_a?(Array)
                new_arr += el.my_flatten(value - 1)
            else
                new_arr << el
            end
        end
        new_arr
    end
end

[1, [2, 3], 4, [5]]

[1,1,2,2,3,4,5]
1 <> 0 1
2 <> 2 3
3 <> 
4 <> 
5 <>

class Array
    def dups
        new_hash = Hash.new {|k, indices|} k[indices]= []}

        self.each_with_index { |ele, i| new_hash[ele] << i }

        new_hash.select {|key, val| val.length > 1 }
    end
end

class Array
    def my_reduce(accumulator = nil, &prc)
        accumulator ||= self[0]

        self.each do |ele|
            accumulator = prc.call(accumulator, ele) 
        end

    accumulator
    end
end

def factorials(n)
    return [1] if n == 1
    factorial = factorials(n - 1)
    factorial << (n - 1) * factorial.last
    factorial
end

3
3 * factorials(3 - 1) [1, 2, 3]
2 * factorials(2 - 1) [1, 1]
1 * factorials(1 - 1) [1]
factorial << [0 * factorials(0)] => [1]
[0!] n = 1 
[0!, 1!] n = 1
[0!, 1!, 2!] n = 2
[0!, 1!, 2!, 3!] n = 3
3! = > 3 * 2 * 1
2! = > 2 * 1
1! = > 1
0! = > 1


