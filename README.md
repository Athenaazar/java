
import java.io.*;
import java.util.zip.*;


public class zipFile {
	public static void main(String[] args) {
		try {
			String file = "READ FIRST.txt";
			String zipFile = "createdZipFile.zip";

			ZipOutputStream zipStream = new ZipOutputStream(new FileOutputStream(zipFile));
			FileInputStream fileStream = new FileInputStream(file);

			// put a new ZipEntry in the ZipOutputStream
			zipStream.putNextEntry(new ZipEntry(file));

			int size = 0;
			byte[] buffer = new byte[1024];

			// read data to the end of the file file and write it to the zip
			// output stream.
			while ((size = fileStream.read(buffer, 0, buffer.length)) > 0) {
				zipStream.write(buffer, 0, size);
			}

			zipStream.closeEntry();
			fileStream.close();

			// Finish zip process
			zipStream.close();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
