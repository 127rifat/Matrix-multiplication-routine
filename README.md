// Matrix-multiplication-routine

#include <iostream>
#include <vector>

// Function to multiply two matrices
std::vector<std::vector<double>> matrixMultiply(const std::vector<std::vector<double>>& A, const std::vector<std::vector<double>>& B) {
    int rowsA = A.size();
    int colsA = A[0].size();
    int rowsB = B.size();
    int colsB = B[0].size();

    // Check if matrices can be multiplied
    if (colsA != rowsB) {
        std::cout << "Matrix multiplication is not possible. Columns of A must be equal to rows of B." << std::endl;
        return std::vector<std::vector<double>>();
    }

    // Initialize the result matrix with zeros
    std::vector<std::vector<double>> result(rowsA, std::vector<double>(colsB, 0.0));

    // Perform matrix multiplication
    for (int i = 0; i < rowsA; ++i) {
        for (int j = 0; j < colsB; ++j) {
            for (int k = 0; k < colsA; ++k) {
                result[i][j] += A[i][k] * B[k][j];
            }
        }
    }

    return result;
}

int main() {
    // Define two matrices A and B
    std::vector<std::vector<double>> A = {{1.0, 2.0, 3.0}, {4.0, 5.0, 6.0}};
    std::vector<std::vector<double>> B = {{7.0, 8.0}, {9.0, 10.0}, {11.0, 12.0}};

    // Multiply matrices A and B
    std::vector<std::vector<double>> result = matrixMultiply(A, B);

    // Display the result
    for (const auto& row: result) {
        for (double val : row) {
            std::cout << val << " ";
        }
        std::cout << std::endl;
    }

    return 0;
}
