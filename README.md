import cv2

def enhance_image_with_clahe(input_image_path, output_image_path):
    # Load the image in grayscale
    image = cv2.imread(input_image_path, cv2.IMREAD_GRAYSCALE)

    if image is None:
        print("Error: Could not read the image.")
        return

    # Create a CLAHE object
    clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8, 8))

    # Apply CLAHE to the image
    enhanced_image = clahe.apply(image)

    # Save the enhanced image
    cv2.imwrite(output_image_path, enhanced_image)
    print(f"Enhanced image saved to {output_image_path}")

    # Display the original and enhanced images
    cv2.imshow('Original Image', image)
    cv2.imshow('Enhanced Image', enhanced_image)

    # Wait for a key press and close the display windows when any key is pressed
    cv2.waitKey(0)
    cv2.destroyAllWindows()

if __name__ == "__main__":
    input_image_path = 'clahe/underwater.jpg'  # Replace with the path to your input image
    output_image_path = 'enhanced_image.jpg'  # Output path for the enhanced image

    enhance_image_with_clahe(input_image_path, output_image_path)
