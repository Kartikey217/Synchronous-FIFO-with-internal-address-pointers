# Synchronous-FIFO-with-internal-address-pointers
This FIFO is a synchronous memory buffer with internal read/write addresses that update automatically. It stores and retrieves data sequentially, maintaining FIFO order without manual pointer control, and supports simultaneous synchronous read and write operations.
This project implements a 16-entry synchronous FIFO (First-In-First-Out) buffer using Verilog HDL. Each memory location stores 8-bit data, and all operations are synchronized to a common clock, ensuring predictable timing and eliminating glitches. The FIFO is designed to maintain the correct order of data, with the oldest data read first, and the newest data written last.

# The FIFO memory is implemented as a shift-register array, where each write inserts a new data element at the next available location, and each read removes the oldest element while shifting the remaining data to maintain the order. An internal 5-bit address counter tracks the number of valid data entries in the FIFO. The full flag triggers when all 16 entries are occupied, and the empty flag triggers when no data is stored, preventing overflow and underflow conditions.

The Verilog module (fifo) includes:

1 clk and reset for synchronous operation,

2 wr_en and rd_en for write and read control,

3 din and dout for 8-bit data input/output,

4 full and empty flags to indicate FIFO status.

# FIFO behavior:

1 Write Operation: Stores din at the next available location if FIFO is not full, increments the internal address counter.

2 Read Operation: Outputs the oldest data from mem[0] if FIFO is not empty, shifts remaining elements, and decrements the internal address counter.

3 Testbench (test_fifo)

4 The testbench verifies the correct functionality of the FIFO module:

5 Clock Generation: 100 MHz clock signal.

6 Reset Task: Initializes FIFO memory, address counter, and output.

7 Write Tasks: write for single-byte writes and write16 for writing all 16 entries to test full condition.

8 Read Tasks: read for single-byte reads and read16 for reading all 16 entries to test empty condition.

* Test Sequence: Resets the FIFO, initializes signals, writes 16 bytes sequentially, and reads 16 bytes in FIFO order.

This project demonstrates a fully synchronous, 16 × 8-bit FIFO with automatic internal address management, proper full/empty flag monitoring, and safe integration with other Verilog modules. It is ideal for digital signal processing, data buffering, and communication interface applications.
