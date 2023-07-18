def firstFit(m, n):
    blockSize = []
    processSize = []
    allocation = [-1] * n
    holes = []  # Danh sách để lưu trữ các giá trị khoảng trống
    hole_str = ""  # Biến chuỗi để xây dựng dòng in hole

    # Nhập vào mảng blockSize
    print("Enter the block sizes:")
    for i in range(m):
        size = int(input("Block size {}: ".format(i + 1)))
        blockSize.append(size)

    # Nhập vào mảng processSize
    print("Enter the process sizes:")
    for i in range(n):
        size = int(input("Process size {}: ".format(i + 1)))
        processSize.append(size)

    for i in range(n):
        for j in range(m):
            if blockSize[j] >= processSize[i]:
                allocation[i] = j
                holes.append(blockSize[j])  # Lưu trữ giá trị hiện tại của khối vào danh sách "hole"
                blockSize[j] -= processSize[i]
                break

    print("Process No.   Process Size    Block no.")
    for i in range(n):
        print(" ", i + 1, "         ", processSize[i], "         ", end=" ")
        if allocation[i] != -1:
            print(allocation[i] + 1)
        else:
            print("Not Allocated")

    # Xây dựng dòng in hole
    for hole in holes:
        hole_str += str(hole) + " "

    # In ra các giá trị của các hole trên cùng một dòng
    print("First-fit: ", hole_str)


# Driver code
if __name__ == '__main__':
    m = int(input("Enter the number of blocks: "))
    n = int(input("Enter the number of processes: "))

    firstFit(m, n)
